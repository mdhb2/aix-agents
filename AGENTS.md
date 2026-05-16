# AGENTS.md

This project uses `aix-agents`.

Before doing any non-trivial task, read:

`.aix/rules/RULES.md`

The active project rules live in:

`.aix/rules/`

The reusable agent pack lives in:

`.agents/`

Available skills live in:

`.agents/skills/`

Runtime artifacts must be written under:

`.aix/artifacts/`

Do not write generated artifacts, intermediate files, handoffs, logs, plans, summaries, or task state outside `.aix/artifacts/` unless explicitly allowed by `.aix/rules/04-write-boundaries.md` or directly requested by the user.

For task state, progress, decisions, and context preservation, use the `planning-with-files` skill by default.
