---
name: aix-map
description: Token-saving repo context workflow for OpenCode. Use this skill whenever user asks coding, debugging, refactor, feature work, or repo understanding that may involve multiple files. Always use this skill for repo-level tasks, architecture questions, endpoint changes, auth fixes, config edits, database work, UI updates, or test-impacting changes, even when user does not explicitly mention context maps.
compatibility:
  tools: Read, Glob, Grep, Edit, Write
---

# aix-map

Goal: reduce token usage by reading indexed repo context first, then reading only relevant source files.

## Core idea

Read `.aix` context before deep code exploration.
Do minimal reads.
Avoid full-repo scan unless required.

## Required workflow

1. Before coding, read `.aix/AI_CONTEXT.md`.
2. From `AI_CONTEXT.md`, choose only 1-2 relevant map files in `.aix/maps/`.
3. Read only source files listed in chosen map files.
4. Do not scan full repo unless:
   - `.aix` missing, or
   - `.aix` outdated, or
   - task cannot be understood from available maps.
5. After coding, update only relevant `.aix` files.
6. Keep `.aix` docs short, factual, AI-friendly.

## Outdated rules

Treat `.aix` as outdated when one or more applies:
- `AI_CONTEXT.md` contradicts current repo layout.
- map files reference missing or renamed files.
- task target area not represented in maps.
- `.aix/recent-changes.md` has no fresh entry for major recent work.

When outdated:
- perform smallest possible targeted scan to recover context.
- update only affected `.aix` docs.

## Read policy

- Prefer map-listed files over discovery scans.
- If map uses globs, expand only needed matches.
- Do not open unrelated files.
- Explain fallback reason when broader scan is unavoidable.

## Update policy after changes

Always do both when relevant:
- append one short line to `.aix/recent-changes.md`.
- update impacted map file(s) when file list/ownership changes.

Do not rewrite entire `.aix` set when only one area changed.

## Writing style for `.aix`

- Short sections.
- Concrete file paths.
- No long narrative.
- No marketing language.

## Map file pattern

Maps must list only files that exist in this repository. Do not add assumed paths, directories, or files that are not present.

When creating or editing a map follow these steps:

1. Run a glob search for candidate files inside repo (e.g., `src/**/*.js`).
2. Include only the concrete matches returned by the glob. If a glob matches nothing, do not add that glob to the map.
3. Prefer explicit file paths to broad globs. If using a glob, expand it and paste the matched file paths into `files:` so the map contains concrete file names.
4. If the map would be empty for this project, omit the map file or leave `files:` empty and document why.

Map schema example (must reference existing files):

```md
Description: One-line area summary.
files:
  - src/api/users.js
  - src/models/user.js
why: One-line reason this map should be chosen.
```

Language: All map files and `.aix` documentation MUST be written in English. Use concise, factual English for `Description` and `why` fields so AI agents and reviewers can parse reliably.

## Quick execution checklist

1. Read `.aix/AI_CONTEXT.md`.
2. Pick 1-2 maps.
3. Read listed files only.
4. Implement change.
5. Update relevant `.aix` docs.


## AIX Pack Compliance
- This skill is part of AIX skill pack.
- User-facing alias: aix-map.
- When user invokes aix-map, use this skill.
- Write generated artifacts under .aix/.
- Before writing generated files, ensure directory exists with mkdir -p .aix.
- Generated files in .aix/ may be overwritten by default.
- Do not write generated files to project root unless explicitly requested.
