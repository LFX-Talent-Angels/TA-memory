# Engine baseline: Locate is exact and free; the chat costs about 4.3k tokens a turn

- **Date:** 2026-11-25
- **Context:** Sprint 3 acceptance ("golden evals runnable with one command; baseline numbers
  recorded in TA-memory") and the ADR-0003 falsifiers (tokens per resolved turn, Locate accuracy),
  measured at the close of the engine work.

## What was measured

One integrated build of TA-agents: the PR stack top `663920a` (Graph-Mapper, Evaluator v0,
all-taxonomy map, discovery map, `bench --suite`) merged with the fix branches `fd6ac75`, `7eae6d3`
and `bf6c9af`. Data: ta-taxonomies pin `1651943`, live Neo4j with all five suites. Chat model:
`azure_ai/claude-sonnet-4-6` via litellm. Cold runs, no neighbour cache.

### Locate (`ta-agent bench --suite <s>`, golden Locate set per suite)

| Suite | Cases | hit@1 | Candidate recall | Model cost | Graph time per case |
|---|---|---|---|---|---|
| ESCO | 12 | 8/8 = 1.00 | 3/3 = 1.00 | $0 | 362 ms |
| O*NET | 11 | 10/10 = 1.00 | – | $0 | 478 ms |
| BLS | 13 | 12/12 = 1.00 | – | $0 | 337 ms |
| JobTech | 12 | 11/11 = 1.00 | – | $0 | 376 ms |
| SFIA | 8 | 7/7 = 1.00 | – | $0 | 707 ms |

With the result cache warm, the same sets give identical answers in 0 ms of graph time.

### Chat (`ta-agent quality`, the local question card, 37 cases)

| Measure | Value |
|---|---|
| Pass | 21/37 |
| Model calls | 122 (3.3 a turn) |
| Tokens | 150,023 in, 8,481 out, 0 reasoning: **about 4,284 a turn** |
| Cost | $0.577 ($0.016 a turn) |
| Time a turn | p50 9.7 s, p95 14.3 s |

The same 37 cases on `dev` (`032359b`) fail on exactly the same 16 cases: no regression from the
engine work.

### Suites

Offline: 1,497 passed. Live (Neo4j): 136 passed.

## What we expected vs. what happened

We expected Locate to cost tokens, because the falsifier is phrased as tokens per resolved
turn. It costs **none**: since the "first lookups decided in code" change, Locate is a
deterministic search with a total order, so the model plays no part in where a title lands. The
tokens go to the conversation around it: planning, phrasing and the tool loop for follow-ups.

The 16 failing quality cases are not wrong answers. The card (written in August) expects an older
behaviour:
- 11 cases: a bare title such as "chef" now answers with that job's skills card (`connect`),
  where the card expects a bare `locate`;
- 2 cases: an ambiguous title such as "nurse" now looks at groups (`get_neighbors`) to offer
  areas, which the card forbids;
- 2 cases: the top hit changed with the data (for example "programmer");
- 1 case: a skill question now connects.

## Why it matters

- **ADR-0003's single-assistant design holds.** Locate accuracy is 1.00 in every suite without a
  model, so nothing argues for a Locate subagent. The chat turn is about 4.3k tokens, almost all
  input (prompt and context), which is the place to look if cost ever matters.
- A quality score is only meaningful against a card kept in step with the behaviour. A stale card
  reports a lower pass rate that is easy to misread as a regression.

## How to apply it

- Rerun with `ta-agent bench --suite <esco|onet|bls|jobtech|sfia>` and
  `python -m talent_angels.cli quality --suite <card.json>` on one fixed commit. Compare against
  `dev` on the same card before calling anything a regression.
- Update the quality card to today's behaviour (skills card on a bare title, area offers on an
  ambiguous title, the new `pathfind_refuse` family) before using its score as a target.
