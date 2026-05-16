---
name: context-map
description: 'Generate a map of all files relevant to a task before making changes'
---

# Context Map

Before implementing any changes, analyze the codebase and create a context map.

## Task

{{task_description}}

## Instructions

1. Search the codebase for files related to this task
2. Identify direct dependencies (imports/exports)
3. Find related tests
4. Look for similar patterns in existing code

## Output Format

```markdown
## Context Map

### Files to Modify
| File | Purpose | Changes Needed |
|------|---------|----------------|
| path/to/file | description | what changes |

### Dependencies (may need updates)
| File | Relationship |
|------|--------------|
| path/to/dep | imports X from modified file |

### Test Files
| Test | Coverage |
|------|----------|
| path/to/test | tests affected functionality |

### Reference Patterns
| File | Pattern |
|------|---------|
| path/to/similar | example to follow |

### Risk Assessment
- [ ] Breaking changes to public API
- [ ] Database migrations needed
- [ ] Configuration changes required
```

Do not proceed with implementation until this map is reviewed.


## AIX Pack Compliance
- This skill is part of AIX skill pack.
- User-facing alias: aix-context-map.
- When user invokes aix-context-map, use this skill.
- Write generated artifacts under .aix/.
- Before writing generated files, ensure directory exists with mkdir -p .aix.
- Generated files in .aix/ may be overwritten by default.
- Do not write generated files to project root unless explicitly requested.
