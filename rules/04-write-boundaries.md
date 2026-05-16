# Write Boundaries

## Default Rule

Generated artifacts must be written under:

```txt
.aix/artifacts/
```

## Allowed Writes Outside `.aix/artifacts/`

Writing outside `.aix/artifacts/` is allowed only when:

1. The user explicitly asks to create or modify project files.
2. The file is part of the actual requested implementation.
3. The active rule allows it.
4. A specific skill exception is declared.
5. Temporary files are created and cleaned up before completion.

## Skill Rule Override

If a skill's original instructions say to write artifacts elsewhere, override that behavior.

The project artifact boundary wins:

```txt
.aix/artifacts/
```

## Source Code Changes

Source code may be changed outside `.aix/artifacts/` only when the task requires modifying the project itself.

Examples:

Allowed:

```txt
src/auth/login.ts
package.json
README.md
```

Not allowed unless explicitly needed:

```txt
random-notes.md
scratch.txt
temporary-plan.md
```

## No Silent Writes

Before writing outside `.aix/artifacts/`, the agent must be able to explain:

- what will be written
- where it will be written
- why it belongs outside `.aix/artifacts/`
