# TA-memory

The **project memory** of Talent Angels: the permanent record of why the project
exists and how it evolved. This is where context lives so future mentees — and AI
coding agents — can understand decisions long after they were made.

This is a **subrepo** of the Talent Angels workspace. Content is **CC-BY-4.0**.

## What lives here

```
proposals/   # the original project proposal and any revisions
decisions/   # accepted ADRs (mirrored from TA-workspace/docs/decisions/)
meetings/    # meetup and sync notes
learnings/   # non-obvious things we learned (gotchas, insights, dead-ends)
timeline.md  # chronological project log
```

## Conventions

- This repo is **append-mostly**: we add to the record, we don't rewrite history.
  Correct mistakes with a new dated note rather than deleting the old one.
- **No personal data.** Never store CVs, cover letters, or anything from the
  local `Mentees/` folder here. Mentors and public handles (from the proposal)
  are fine; private contact details beyond what's already public are not.
- Accepted ADRs are copied here from `TA-workspace/docs/decisions/` so the
  permanent record is complete.
- Date entries `YYYY-MM-DD`.

## Read first

1. `proposals/original-proposal.md` — the source of truth for scope and intent.
2. The workspace policy: `../TA-workspace/CLAUDE.md` (git, DCO).

## Git

Branch + PR, **`git commit -s`** (DCO). Never push to `main`.
