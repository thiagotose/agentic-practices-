# agentic-practices

Reusable, portable practices for agent-augmented repositories.

This repository contains the canonical definition of **general agentic practices** — starting with chronicling — that improve reasoning quality across any codebase or personal operating system.

## Principles

- **Portable first** — works in code monorepos, personal workflow repos, client projects, and open source.
- **Minimal friction** — Markdown + git as the foundation.
- **Human + agent readable** — structured enough for LLMs, pleasant for humans.
- **Evolves independently** — decoupled from any single product or monorepo.

## Current Practices

- **Chronicle** — Daily capture of decisions, events, agent actions, and reusable insights (`chronicle/`).

## Quick Start

1. Clone this repo
2. Copy the `chronicle/` folder into your target repository
3. Start writing daily entries using the template in `chronicle/templates/daily.md`
4. Update `INDEX.md` as entries accumulate

See `docs/extraction-guide.md` and `examples/` for real usage patterns.

## Structure

```
agentic-practices/
├── README.md
├── chronicle/
│   ├── contract.md
│   └── templates/
├── playbooks/
├── skills/
│   └── agentic-chronicle/
├── examples/
│   ├── execute-ai/
│   └── personal-workflows/
└── docs/
```

## Status

**v0.1.0** – Initial release (Phase 5 complete). Practices have been validated across two different repository types.

## License

MIT

---

**Next**: Expand the Hermes skill and add optional CLI tooling.