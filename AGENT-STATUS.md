# Execute AI — Agent Status Dashboard

Last updated: 2026-05-27

This file gives a quick overview of all active agents, their schedules, and last known run status.

## Active Agents

| Agent                    | Type       | Schedule                  | Output Folder     | Last Known Run | Status     | Notes |
|--------------------------|------------|---------------------------|-------------------|----------------|------------|-------|
| **Chronicler**           | Scheduled  | Daily 08:00 EST (`0 12 * * *`) | `chronicle/`      | 2026-05-26     | ✅ Active  | Fully operational |
| **Architect**            | Scheduled  | Weekly Sun 20:00 EST (`0 1 * * 0`) | `architecture/`   | 2026-W23       | ✅ Active  | W23 memo generated |
| **Closer**               | Scheduled  | Weekly Mon 09:00 EST (`0 14 * * 1`) | `positioning/`    | 2026-W23       | ✅ Active  | W23 memo generated |
| **Platform Researcher**  | On-demand  | None                      | `research/`       | 2026-05-27     | ✅ Ready   | Available via delegate_task or direct call |

## Shared Skills

| Skill            | Purpose                              | Used By                  | Status |
|------------------|--------------------------------------|--------------------------|--------|
| `agent-core`     | Philosophy, voice, output standards  | All agents               | ✅ Active |
| `agent-runtime`  | Cron patterns, naming, summaries     | All agents               | ✅ Active |

## Cron Jobs

| Job Name                    | Schedule         | Profile    | Next Run              | Status |
|-----------------------------|------------------|------------|-----------------------|--------|
| `chronicler-daily-synthesis`| `0 12 * * *`     | chronicler | Daily                 | Active |
| `architect-weekly`          | `0 1 * * 0`      | chronicler | Next Sunday           | Active |
| `closer-weekly`             | `0 14 * * 1`     | chronicler | Next Monday           | Active |

## Quick Manual Invocation

```bash
# Run Chronicler manually
hermes cron run chronicler-daily-synthesis

# Research something on-demand
hermes chat -q "Research best options for X" \
  --skills execute-ai-platform-researcher \
  --profile chronicler
```

## Notes
- All agents follow "Agents propose, humans dispose"
- All scheduled agents deliver short Telegram summaries
- Research outputs are durable and stored in `research/`

Update this file whenever a new agent is added or a schedule changes.