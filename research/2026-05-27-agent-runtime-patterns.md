# Research: Agent Runtime Patterns — 2026-05-27

## Question
What are the emerging patterns for running multiple coordinated AI agents in production, especially for small founder-led teams that want leverage without full autonomy?

## Options Considered

| Option                    | Type              | Maturity | Pros                                      | Cons                                          | Fit for Thiago's Setup | Score |
|---------------------------|-------------------|----------|-------------------------------------------|-----------------------------------------------|------------------------|-------|
| Single shared profile + scheduled agents | Hermes-style      | Medium   | Simple, low overhead, easy to reason about | Limited isolation between agents              | High                   | 9/10  |
| Dedicated profiles per agent            | Hermes-style      | Medium   | Strong isolation, different voices/memories | More management overhead                      | Medium                 | 7/10  |
| Fully autonomous swarms                 | LangGraph / CrewAI| High     | Powerful for complex workflows            | Hard to debug, risk of runaway behavior       | Low                    | 3/10  |
| Subagent delegation model               | Hermes delegate_task | Medium | Clean handoff, focused research agents   | Still requires careful scoping                | High                   | 8/10  |

## Recommendation
**Keep the current model** (shared `chronicler` profile + `delegate_task` for researchers) for the next 2–3 months. It balances simplicity with the ability to spin up specialized researchers when needed.

Only move to dedicated profiles if isolation or voice differentiation becomes a real pain point.

## Risks & Unknowns
- As the number of agents grows, profile and cron management could become fragmented.
- No strong precedent yet for "agent runtime" as a first-class concept in small teams.

## Sources
- Current `agentic-practices` implementation
- Hermes delegation patterns
- Patterns observed in LangGraph / CrewAI communities (used as contrast)