# Sprint Notes — Agent Intelligence & Search Ranking
**Date:** 2026-09-22

## What was built

### TA-agents — Agentic tool loop + session memory (PR #40, `feature/agent-intelligence`)

- **Real `run_tool_loop()`**: LLM-driven multi-round tool loop. Each turn the LLM chooses which graph tool to call (`search_nodes` or `get_neighbors`), executes it, gets the result back, and decides whether to call another tool or produce a final answer. Previously this was all heuristic / mock.
- **`_first_json_object()`**: Brace-depth parser replacing greedy regex — safely handles multi-JSON LLM responses.
- **First-round enforcement**: If the LLM tries to answer before searching, the agent forces a `search_nodes` call. Prevents hallucinated answers.
- **`MemorySaver` checkpointer**: `build_graph()` gains `thread_id`; attaches a LangGraph checkpointer for cross-turn state.
- **Session memory**: `session_id` in `QueryRequest`/`QueryResponse`. `load_session`/`save_session` wraps every turn. `_apply_outcome_bindings()` updates per-suite node bindings so the user does not have to re-specify context on every message.
- **MEMORY.md injection**: The assistant's memory (USER.md, GOALS.md, etc.) is now injected into all three LLM system prompt sites (phrase, synthesize, agent_notes).

### TA-agents — Search ranking fixes (PR #41, `fix/search-ranking`)

- **`unique_enough` threshold**: Old logic only auto-selected on tier 0 (exact pref) or tier 3 (exact alt). New: `top_tier < second_tier` — any clear tier gap triggers auto-select. Eliminates cases where "web developer" (tier 1) stayed ambiguous with "3D modeller" (tier 4 via alt).
- **`group_and_sort_locate()` in tool loop**: Critical missing piece. The tool loop called `locate()` (which returns Neo4j's raw sort order — shortest pref_label first) without ever calling `group_and_sort_locate()`. Fixed by adding the reranking call inside `_execute_tool()`.

### TA-taxonomies — Tier merge fix (PR #15, `fix/search-ranking`)

- **Root cause of "nurse → nanny/midwife"**: ESCO has `nanny` and `midwife` with "nurse" as historical alt_labels. The search pipeline exited at Tier 2 (exact alt) without ever reaching Tier 4 (pref_label contains "nurse"). `registered nurse` was never seen.
- **Fix**: Remove the Tier 2 early exit. Merge Tier 2 (alt_label exact matches) into the Tier 4 (contains) candidate pool. Return both to TA-agents for `lexical_rank()` re-ordering. `registered nurse` (pref_label contains "nurse", tier 1 via token match) now ranks above `nanny` (alt_label exact, tier 3).
- Applied identically to ESCO and O*NET suites.

### TA-taxonomies — Hybrid search (PR #16, `feat/hybrid-search`)

- **Tier 5 semantic fallback**: When Tiers 1–4 return nothing (no keyword overlap), a hybrid BM25 + vector ANN search runs and results are merged via Reciprocal Rank Fusion (RRF).
- **Model**: `all-MiniLM-L6-v2` (384 dims, Apache-2.0, ~80 MB). One-time batch job (`embed.py`) embeds all node `pref_label` strings and writes them to Neo4j; a vector index is created automatically.
- **Graceful degradation**: If the index has not been built, Tier 5 returns `not_found` with a `vector_index_missing` warning — no crash, no regression to existing behavior.
- **Contract unchanged**: `search_nodes(text, kind)` → `ToolResult`. TA-agents never configures the retrieval strategy; hybrid is an internal suite detail.
- **`CONF_HYBRID = 0.75`**: Declared policy confidence (between `CONF_CONTAINS=0.70` and `CONF_CASEFOLD_UNIQUE=0.85`). Never a raw similarity score.

## Gaps identified (live testing)

8 gaps were found during live testing of the agentic loop. Prioritized:

| ID | Description | Priority | Status |
|---|---|---|---|
| GAP 1 | "nurse" returns nanny/midwife at top | P0 | ✅ Fixed (tier merge + rerank) |
| GAP 2 | Tool loop over-fetches neighbors on LOCATE queries | P1 | Open |
| GAP 3 | No-keyword queries return not_found (Tier 5 needed) | P1 | ✅ Fixed (hybrid search) |
| GAP 4 | Pathfind silently returns skills instead of not_implemented | P1 | Open |
| GAP 5 | Terse answers on multi-suite results (merge_answers template) | P2 | Open |
| GAP 6 | Goal intent not persisted across turns | P2 | Open |
| GAP 7 | Suite selection not confirmed before querying | P2 | Open |
| GAP 8 | USES_SOFTWARE warning leaks into user-facing response | P3 | Open |

## Live test results (as of 2026-09-22)

| Query | Expected | Result |
|---|---|---|
| "find a nurse" (ESCO) | nurse occupations at top | ✅ nurse assistant / specialist nurse / advanced nurse practitioner |
| "find a doctor" | auto-select | ✅ auto-selects "specialised doctor" |
| "software developer" | exact match 0.95 | ✅ |
| "sofware develper" (typo) | software developer | ✅ |
| "what does a data scientist do?" | data scientist exact | ✅ |
| "find a developer" | ambiguous, 25 results | ✅ |
| "registered nurse" (O*NET) | found | ✅ "Registered Nurses" |
| "someone who helps sick people" | not_found (no index yet) | ✅ graceful fallback |
| Session continuity | cross-turn state | ✅ |

## Architecture direction

- **KG is the sole source of taxonomy fact**. Vector embeddings are derived from node `pref_label` strings, not invented by an LLM. `confidence` is a declared policy value, never a raw similarity score.
- **Hybrid search is an internal suite detail**. TA-agents calls `search_nodes(text)` and gets a `ToolResult`. It never configures the retrieval strategy.
- **`group_and_sort_locate()` is mandatory after every `locate()` call**. This is now documented in `ARCHITECTURE.md`.
- **Next sprint**: Fix GAP 4 (pathfind guard), GAP 2 (intent-gated neighbor fetching), GAP 5 (multi-suite answer template), run ESCO embed job against Docker Neo4j to activate Tier 5.

## Open items for next sync

- Run `uv run python -m ta_taxonomies.suites.esco.embed` against Docker to build vector index and verify semantic queries
- Fix GAP 4: add pathfind guard at start of `run_tool_loop()` — detect `cap=pathfind`, return `capability_not_implemented:pathfind`
- Fix GAP 2: pass intent to tool loop to prevent over-fetching neighbors on pure LOCATE queries
