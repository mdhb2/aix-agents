# AIX Skill Pack

Meta skill. Defines AIX-wide conventions for all skills in this repository.

## Purpose

- Enforce user-facing alias pattern `aix-<skill-name>`.
- Keep real skill folder names unchanged under `skills/<skill-name>/`.
- Standardize all generated artifacts under `.aix/`.

## AIX Conventions

1. Alias rule
   - Every skill has user-facing alias: `aix-<skill-name>`.
   - Example: `brainstorming` -> `aix-brainstorming`.

2. Canonical skill identity
   - Real skill name and folder stay unchanged.
   - Do not rename folders to include `aix-` prefix.

3. Alias scope
   - `aix-` prefix is invocation alias only.
   - Alias does not change underlying skill implementation identity.

4. Output location
   - All generated files must be written under `.aix/`.
   - Examples:
     - `.aix/DEVELOPMENT_PLAN.md`
     - `.aix/CODEBASE_MAP.md`
     - `.aix/VERIFY_REPORT.md`
     - `.aix/CHANGELOG_DRAFT.md`

5. Directory creation
   - Before writing generated files, ensure directory exists:
     - `mkdir -p .aix`

6. Overwrite behavior
   - Generated files under `.aix/` may be overwritten by default.

## Non-Goals

- Do not rename existing skill directories.
- Do not merge skills.
- Do not create hard dependencies between skills.
- Do not modify unrelated behavior.

## Compliance Note For Skills

Each `skills/*/SKILL.md` should include `## AIX Pack Compliance` section that states:

- Skill is part of AIX skill pack.
- User-facing alias is `aix-<skill-name>`.
- When user invokes alias, use that skill.
- Generated artifacts go under `.aix/`.
- Do not write generated files to project root unless explicitly requested.
