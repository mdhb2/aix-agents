# File Naming

## General Rule

Use lowercase kebab-case for generated files and folders.

Good:

```txt
implementation-plan.md
api-contract.json
refactor-summary.md
```

Bad:

```txt
Implementation Plan.md
apiContract.json
final FINAL.md
```

## Task Folder Naming

Use:

```txt
<yyyymmdd-hhmm-task-slug>
```

Example:

```txt
20260516-1430-refactor-auth-flow
```

## Slug Rules

Slugs must be:

- lowercase
- kebab-case
- short but meaningful
- stable for the task

Avoid vague names like:

```txt
task
new-task
misc
work
final
```

Prefer names like:

```txt
refactor-auth-flow
create-agent-rules
review-payment-api
```

## Timestamps

Use local project/user time unless instructed otherwise.

Default timestamp format:

```txt
yyyymmdd-hhmm
```
