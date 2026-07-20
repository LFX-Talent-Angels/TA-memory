# Project Timeline

Chronological log of notable project events. Newest entries on top. Date format
`YYYY-MM-DD`.

## 2026

- **2026-07-19** — **Sprint 2 closed; the team's architecture adopted.** The
  mentee team's joint proposal — one main assistant owning the goal, with
  Locate/Connect/Pathfind/Evaluate as skills + tools — accepted as
  [ADR-0003](./decisions/0003-agent-plus-skills-architecture.md);
  `TA-workspace/docs/architecture/SYSTEM.md` rewritten around it. ADR-0004
  (repo topology) and ADR-0005 (tech stack: Python/Neo4j/LangGraph/Claude/
  FastAPI, pgvector provisional) proposed, pending team confirmation at the
  next sync. The Evaluator advanced from "future agent" to candidate skill
  (`score_paths` enters the suite contract). Review feedback posted on the
  three Sprint 2 architecture PRs (TA-lab #7, #8, #12) with concrete paths to
  merge each as the sprint record. Sprint 3 brief published
  (`docs/sprints/sprint-03-suites-and-assistant.md`) — written in-repo, unlike
  Sprint 2's slide-only assignment.
- **2026-07-19** — **Repo topology expanded** per ADR-0004: `TA-taxonomies`
  created (one suite per taxonomy behind a shared contract: `search_nodes`,
  `get_neighbors`, `enumerate_paths`, `score_paths`; consumed by `TA-agents`
  as a versioned library) and `TA-app` created as the chat-frontend
  placeholder (stack TBD via its own ADR). `TA-agents` restructured from
  three-agent packages to `assistant/` + `skills/`. Branch protection applied
  to both new repos; accepted ADRs (0003, 0006) mirrored into this repo.
- **2026-07-19** — **Sprint 1 closed; taxonomy data sources decided**
  ([ADR-0006](./decisions/0006-taxonomy-data-sources.md)). All four mentee
  taxonomy slices merged into `TA-lab` (O*NET #1, ESCO #2, SFIA #3, BLS #6),
  plus the Lightcast slice-turned-evidence (#13). Verdict: **Lightcast
  dropped** (cost $41–50k/yr, licence §2.3 names "artificial intelligence
  purposes", free tier killed with 3 days' notice); **SFIA structure-only**
  (codes/names/levels, never its prose); **Sweden JobTech** takes the fifth
  slot (live-postings signal, CC0). Source-by-source terms recorded in
  `TA-workspace/docs/architecture/TAXONOMIES.md`. Homologation of the four
  slices to a common format underway (#14 merged; #15–#17 in mentee
  self-review). Key reusable findings: entity resolution is a hard
  prerequisite (people type job titles, not codes); ESCO is structurally
  binary (any weighting is our declared policy); every node carries
  `source` + `source_id`; store the pointer, fetch the payload at runtime.
- **2026-07-02 → 07-13** — **Sprint 2 architecture proposals** submitted in
  `TA-lab` (#7 spec-driven docs + ADRs; #8 agent/subagent/skill/tool topology;
  #12 main-assistant model + diagrams), followed by the team's joint
  presentation ("Rethinking the Agent Architecture") converging on the
  assistant + skills model and the Neo4j/LangGraph/Claude/FastAPI/pgvector
  stack.
- **2026-06-21 → 06-25** — **Sprint 1 slices submitted** in `TA-lab`: one
  knowledge-graph slice per mentee per taxonomy (O*NET, ESCO, SFIA, BLS) —
  all four independently chose Neo4j + Cypher, the convergence that later
  anchored the graph-store decision (ADR-0005).
- **2026-06-16** — **Sprint 1 kicked off**: brief published
  (`TA-workspace/docs/sprints/sprint-01-knowledge-graphs.md`) with the
  exercise in `TA-lab/exercises/sprint-01-taxonomy-graph/`.
- **2026-06-15** — Methodology shift to **agent-driven development** +
  **outcome-based roadmap** ([ADR-0002](./decisions/0002-agent-driven-outcome-based.md)).
  Original 9-deliverable waterfall archived in
  [`roadmap/2026-original-9-deliverable-roadmap.md`](./roadmap/2026-original-9-deliverable-roadmap.md);
  current plan (from PM Noemí Muñiz's roadmap) in
  [`roadmap/2026-outcome-based-roadmap.md`](./roadmap/2026-outcome-based-roadmap.md).
  Added `TA-lab` sandbox and project skills (`ta-ship`, `ta-define`, `ta-skill`).
- **2026-06-15** — 2026 mentee cohort selected. Selection funnel:
  **99 registered → 35 pre-selected → 11 interviewed → 4 selected.**
- **2026-06-15** — Meta-repo skeleton created for the `LFX-Talent-Angels` org:
  `TA-workspace` (meta), `TA-agents` (code), `TA-resources` (education),
  `TA-memory` (this repo). Original proposal archived in
  `proposals/original-proposal.md`. Governance set to LFDT standard (Apache-2.0
  for code, CC-BY-4.0 for content, DCO sign-off, Contributor Covenant CoC).
