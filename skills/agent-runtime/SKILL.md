---
name: agent-runtime
description: "Shared runtime primitives for Execute AI agents. Handles cron patterns, output file naming, Telegram summary standards, profile usage, and mechanical consistency across all agents."
version: 1.0.0
author: Thiago
---

# Agent Runtime (Mechanical Layer)

This skill contains the **operational and mechanical standards** for all Execute AI agents. It is the companion to `agent-core` (which focuses on philosophy and voice).

Any new or existing agent should follow the patterns defined here.

## Cron Schedule Standards

| Agent Type       | Recommended Schedule     | Reasoning |
|------------------|--------------------------|---------|
| Daily synthesis  | `0 12 * * *` (08:00 EST) | Early enough to capture overnight activity before the workday |
| Weekly reflection| `0 1 * * 0` (Sun 20:00 EST) | End of weekend reflection, before new week starts |
| Weekly positioning | `0 14 * * 1` (Mon 09:00 EST) | Monday morning, after Architect has run |
| On-demand        | No cron                  | Called via `delegate_task` or direct invocation |

All cron jobs should use:
- `--profile chronicler`
- `--workdir /root/agentic-practices`
- `--deliver telegram`

## Output File Naming Convention

| Folder          | File Format                     | Example |
|-----------------|----------------------------------|---------|
| `chronicle/`    | `YYYY-MM-DD.md`                 | `2026-05-26.md` |
| `architecture/` | `YYYY-WW.md`                    | `2026-W23.md` |
| `positioning/`  | `YYYY-WW.md`                    | `2026-W23.md` |
| `research/`     | `YYYY-MM-DD-topic-slug.md`      | `2026-05-27-agent-runtime-patterns.md` |

Always use **newest first** in `INDEX.md` files.

## Telegram Summary Standards

Every scheduled agent (Chronicler, Architect, Closer) must produce a short Telegram summary with this structure:

```
[Emoji] [Agent Name] – [Week/Date] Summary

• Bullet 1 (most important)
• Bullet 2
• Bullet 3
• ...
• Next: [Clear next action or thread]
```

Rules:
- Maximum 6 bullets (ideally 4–5)
- Lead with the highest-signal item
- Always end with a "Next:" line
- Use bold sparingly for key terms
- Keep tone consistent with Thiago's direct voice

## Profile Usage

- Default: All agents run under the `chronicler` profile unless isolation is explicitly needed.
- Future dedicated profiles should only be created when voice, memory, or security isolation is required (document the reason).

## Error Handling & Logging

- If an agent run fails or produces low-quality output, log the issue in the relevant `INDEX.md` or a `notes/` file rather than silently skipping.
- Agents should prioritize **clarity over completeness** when data is missing.

## Invocation Patterns

**Scheduled (via cron):**
```bash
hermes cron create "<schedule>" \
  --name "<name>" \
  --profile chronicler \
  --skill <agent-skill> \
  --workdir /root/agentic-practices \
  --deliver telegram
```

**On-demand (Platform Researcher or future specialists):**
```bash
hermes chat -q "<research question>" \
  --skills execute-ai-platform-researcher \
  --profile chronicler
```

Or via `delegate_task` from another agent.

## Adding a New Agent (Checklist)

When creating a new agent:

1. Create skill in `skills/execute-ai-<name>/SKILL.md`
2. Follow naming and schedule standards in this runtime skill
3. Create output folder + `INDEX.md`
4. Add entry to `AGENTS.md`
5. Create cron job (if scheduled)
6. Update `AGENT-STATUS.md` (see dashboard)

This runtime layer keeps mechanical details consistent so new agents can be added with minimal friction.