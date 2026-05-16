# Agent Rules Index

Read these rules in order:

1. `00-aix-init.md`
2. `_rule-template.md`
3. `00-skill-routing.md`
4. `01-artifact-boundary.md`
5. `02-planning-with-files.md`
6. `03-file-naming.md`
7. `04-write-boundaries.md`
8. `05-communication-caveman.md`

These rules override skill-local rules when there is a conflict, unless an explicit exception is defined.

The active artifact boundary is:

```txt
.aix/artifacts/
```

The default task/progress/context skill is:

```txt
planning-with-files
```

Canonical runtime rule copy list:

```txt
rules/registry.json
```
