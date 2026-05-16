# AIX Init

## Purpose

Bootstrap runtime folders and active rules in target project.

## Run Order

Run this rule first, before other rules.

## Idempotency

Initialization marker:

```txt
.aix/.initialized-by-aix-agents
```

Marker format is JSON (versioned).

If marker exists, do nothing.

## Init Steps

If marker does not exist:

1. Create `.aix/`.
2. Create `.aix/artifacts/`.
3. Create `.aix/rules/`.
4. Read canonical rule list from `rules/registry.json`.
5. Copy listed rule files from source `rules/` to `.aix/rules/`.
6. Exclude `00-aix-init.md` from runtime copied rules.
7. Copy mode is `copy_if_missing` (do not overwrite existing files).
8. Create `.aix/rules/RULES.md` with runtime router content.
9. Write marker `.aix/.initialized-by-aix-agents` with JSON:

```json
{
  "version": 1,
  "initializedAt": "yyyy-mm-ddThh:mm:ssZ",
  "source": ".agents/aix-agents",
  "copyMode": "copy_if_missing",
  "rulesRegistry": ".agents/aix-agents/rules/registry.json"
}
```

## RULES.md Content

Create `.aix/rules/RULES.md` with this content:

```md
# RULES.md

This project uses `aix-agents`.

Before doing any non-trivial task, read:

`.aix/rules/README.md`

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

For communication style and token efficiency, apply `.aix/rules/05-communication-caveman.md`.
```
