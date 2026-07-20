# ADR numbers collide under parallel agent sessions

- **Date:** 2026-07-19
- **Context:** closing Sprint 1 (taxonomy data sources) and Sprint 2 (agent
  architecture) in parallel work sessions.

## What we expected vs. what happened

Two work sessions each needed "the next ADR number" and both minted
**ADR-0003** — one for the taxonomy data-sources decision, one for the
agent-architecture decision. Both were correct locally; the collision only
surfaced when the second branch tried to merge into `main`.

## Why it matters

ADR numbers become *references* the moment they're used: by the time the
collision surfaced, "ADR-0003 = agent+skills" was already cited from
`TA-agents`, `TA-taxonomies`, and three PR review comments to mentees, while
"ADR-0003 = data sources" was cited from `TAXONOMIES.md` and the Sprint 1
brief on `main`. Renumbering is not a rename — it's a reference migration,
and the cost is proportional to how far the number has already traveled.

Resolution rule that worked: **renumber the side with the fewest external
references** (the data-sources ADR became 0006 because its references all
lived inside one repo's `main`, while the agent ADR's number had propagated
across three repos and published PR comments).

## How to apply it

- Merge decision PRs **fast** — an unmerged ADR is an unreserved number.
- Before minting a number, `git fetch` and check `origin/main`'s
  `docs/decisions/` *and* open PRs touching it.
- In parallel-session work, treat the ADR number as claimed only once it's on
  `main`; until then, cite decisions by slug ("the data-sources ADR"), not by
  number.
- This is the same advice we gave the mentees about their three parallel
  Sprint 2 architecture PRs: unmerged decisions diverge silently.
