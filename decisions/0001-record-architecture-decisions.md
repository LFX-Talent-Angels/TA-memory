# ADR-0001: Record architecture decisions

- **Status:** Accepted
- **Date:** 2026-06-15
- **Deciders:** Mentors
- **Source:** `TA-workspace/docs/decisions/0001-record-architecture-decisions.md`

> This is the permanent **mirror** of the workspace ADR. Accepted ADRs are copied
> here so the project memory holds the full record.

## Context

Talent Angels is built by a rotating set of mentees over a 26-week program.
Decisions about the graph store, LLM, taxonomies, and orchestration will be made
incrementally and need to be discoverable later — by future mentees and by AI
coding agents reading the repo.

## Decision

Significant, cross-cutting decisions are recorded as **Architecture Decision
Records (ADRs)** in `TA-workspace/docs/decisions/` and mirrored here in
`TA-memory/decisions/`.

## Consequences

- New significant decisions get a numbered ADR.
- The permanent record lives in `TA-memory`.
- AI agents consult ADRs (instructed via `CLAUDE.md` / `AGENTS.md`).
