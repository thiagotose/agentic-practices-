# Agentic Chronicle Contract (v0.1)

> This is the canonical, portable version of the contract originally drafted in Phase 1 inside `execute-ai`.

(See the original internal draft for full rationale and Phase 1 validation notes.)

## Core Principle

Every significant event, decision, or state change should be captured once, stored durably, and queryable later.

## What Gets Chronicled

Decisions, status changes, external events, agent actions, risks/blockers (required). Commits/PRs and routine reviews (optional).

## Recommended Structure

```
chronicle/
├── YYYY-MM-DD.md
├── INDEX.md
└── decisions/          # optional
```

## File Format

See `templates/daily.md` for the current template.