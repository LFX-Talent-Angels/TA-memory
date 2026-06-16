# Original roadmap — 9-deliverable / week-based plan (archived)

> **Status: superseded** by [`2026-outcome-based-roadmap.md`](./2026-outcome-based-roadmap.md)
> on 2026-06-15. Preserved here as the historical record. This is the plan as
> written in the original proposal (`../proposals/original-proposal.md`).

The original plan was a sequential, week-by-week waterfall of 9 deliverables over
the 26-week program:

| #  | Deliverable                | Weeks |
| -- | -------------------------- | ----- |
| 1  | Understand Knowledge Graphs | 2    |
| 2  | Define purpose & scope      | 4    |
| 3  | System Prompt Design        | 2    |
| 4  | Choose LLM                  | 2    |
| 5  | Tools & Integrations        | 3    |
| 6  | Memory System               | 3    |
| 7  | Orchestration               | 3    |
| 8  | User Interface              | 3    |
| 9  | Testing & Events            | 3    |

Three virtual meetups: end of weeks 10, 19, and 26.

## Why it was superseded

With the shift to **agent-driven development** (see
`../decisions/0002-agent-driven-outcome-based.md`), committing the full 26 weeks
up front stopped making sense: agent-driven work is faster and the highest-value
early effort is **setup and stack/framework definition**, not a fixed waterfall.
The team moved to an **outcome-based NOW/NEXT/LATER** roadmap where only the next
1-2 sprints are committed and the rest is refined each sprint, with the agent
milestones (Locator → Connector → Pathfinder → Evaluator) as the fixed north star.

The 9 deliverables above are not discarded — they are folded in as the *topics*
that the committed sprints and the emerging/directional phases draw on.
