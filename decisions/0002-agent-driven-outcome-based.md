# ADR-0002: Agent-driven development + outcome-based roadmap

- **Status:** Accepted
- **Date:** 2026-06-15
- **Deciders:** Mentors (roadmap proposed by PM Noemí Muñiz)
- **Source:** `TA-workspace/docs/decisions/0002-agent-driven-outcome-based.md`

> Permanent mirror of the workspace ADR.

## Context

The original proposal was a week-by-week waterfall of 9 deliverables over 26
weeks. AI-assisted coding has since matured into **agent-driven** development,
moving the bottleneck from writing code to **setup, stack/framework definition,
and clear specs**.

## Decision

1. **Agent-driven development** is the project's explicit model (documented in
   `CLAUDE.md` / `README` / onboarding). Mentees drive coding agents and own
   what they submit (review + test + DCO).
2. **Outcome-based NOW/NEXT/LATER roadmap** — only Sprints 1–2 committed; agents
   Locator → Connector → Pathfinder → Evaluator are the fixed north star. Source
   archived at `../roadmap/2026-outcome-based-roadmap.md`.
3. **Early sprints prioritize foundations + stack.** Sprint 1 = research + build a
   taxonomy graph (in `TA-lab`); Sprint 2 = LLM + tools + memory.

## Consequences

- `TA-workspace/ROADMAP.md` is the living plan; original waterfall preserved at
  `../roadmap/2026-original-9-deliverable-roadmap.md`.
- The 9 deliverables become topics, not a fixed schedule.
