# Execute AI Agent System — Usage Guide

This document explains how the agent ecosystem in `agentic-practices` works.

## Overview

Four agents run from this repo:

| Agent                    | Type          | Cadence            | Output Location       | Purpose |
|--------------------------|---------------|--------------------|-----------------------|---------|
| **Chronicler**           | Scheduled     | Daily 08:00 EST    | `chronicle/`          | Daily synthesis of what happened across all repos |
| **Architect**            | Scheduled     | Weekly (Sun)       | `architecture/`       | Systems thinking, design proposals, structural recommendations |
| **Closer**               | Scheduled     | Weekly (Mon)       | `positioning/`        | Positioning, messaging, case studies, outbound prep |
| **Platform Researcher**  | On-demand     | As needed          | `research/`           | Deep research on tools, platforms, and infrastructure |

All agents follow the core philosophy:

> **"Agents propose, humans dispose."**

They generate high-quality proposals and artifacts. Thiago decides what gets used, published, or acted upon.

## Shared Core

All agents inherit principles from `skills/agent-core/SKILL.md`:
- Thiago’s direct, energetic, systems-oriented voice
- Structured, scannable outputs
- Grounded in real work only
- Durable file-based outputs (not just chat)

## How to Invoke Agents

### Scheduled Agents
These run automatically via cron:
- Chronicler → `hermes cron list` to see status
- Architect & Closer → run on their weekly schedules

### On-Demand Researcher
```bash
hermes chat -q "Research the best current options for [topic]" \
  --skills execute-ai-platform-researcher \
  --profile chronicler
```

Or via `delegate_task` from another agent.

### Manual Runs (for testing)
```bash
hermes cron run <job_id>
```

## Repo Structure

```
agentic-practices/
├── AGENTS.md                    ← This file
├── chronicle/                   ← Daily logs
├── architecture/                ← Weekly architecture memos
├── positioning/                 ← Weekly positioning & outbound work
├── research/                    ← On-demand research outputs
├── skills/
│   ├── agent-core/              ← Shared primitives
│   ├── execute-ai-chronicler/
│   ├── execute-ai-architect/
│   ├── execute-ai-closer/
│   └── execute-ai-platform-researcher/
└── playbooks/                   ← Planning & methodology docs
```

## Agent Handoff Patterns

- **Chronicler** → feeds **Architect** (Architect reads recent chronicles)
- **Architect** → feeds **Closer** (Closer reads architecture decisions for positioning)
- **Any agent** → can call **Platform Researcher** when deep research is needed

## Best Practices

1. Push work in `execute-ai` and `personal-workflows` regularly so agents have real material to work with.
2. Review agent outputs before acting on them.
3. Keep agent skills versioned and in this repo.
4. When creating new agents, follow the same structure and philosophy.

## Current Status (as of May 2026)

- All four agents initialized
- Chronicler, Architect, and Closer have active cron jobs
- Platform Researcher is available on demand

This system is designed to be lightweight, transparent, and easy to extend.