---
name: agentic-chronicle
description: "Hermes skill that enables an agent to write and maintain daily chronicle entries according to the agentic-practices contract."
version: 0.1.0
author: agentic-practices
license: MIT
tags: [chronicle, agentic, logging, decisions]
---

# Agentic Chronicle Skill

This skill turns any Hermes agent into a capable **Chronicler**.

## What the skill provides

- Reading of the current `chronicle/` folder
- Generation of a properly formatted daily entry
- Updating of `INDEX.md`
- Respect for the official contract

## Usage

```bash
hermes chronicle                    # interactive mode
hermes chronicle --date 2026-05-27  # specific date
hermes chronicle --auto             # let the agent decide what to include
```

## Implementation notes

The actual procedure, voice rules, and safety guidelines live in the full skill file (to be expanded in v0.2).

For now, this skill signals that the `agentic-practices` repo provides first-class Hermes integration.