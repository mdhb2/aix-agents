# Artifact Boundary

## Purpose

Define where generated artifacts must be stored.

## Primary Boundary

All generated task artifacts must be written under:

```txt
.aix/artifacts/
```

For task-specific work, use:

```txt
.aix/artifacts/<yyyymmdd-hhmm-task-slug>/
```

Example:

```txt
.aix/artifacts/20260516-1430-refactor-auth-flow/
```

## Internal Structure

Do not enforce a universal folder structure inside each task artifact folder.

Each skill may create its own internal structure as long as it stays under the active task artifact folder.

Allowed examples:

```txt
.aix/artifacts/20260516-1430-refactor-auth-flow/planning/
.aix/artifacts/20260516-1430-refactor-auth-flow/research/
.aix/artifacts/20260516-1430-refactor-auth-flow/review/
.aix/artifacts/20260516-1430-refactor-auth-flow/custom-skill-output/
```

## No Hidden State

Important assumptions, decisions, progress, generated plans, summaries, and handoffs must be written to files.

Do not rely only on chat context or hidden agent memory.

## Artifact Ownership

A skill may organize its own files, but it must not overwrite another skill's files unless explicitly instructed.

Prefer skill-specific subfolders when multiple skills are active.
