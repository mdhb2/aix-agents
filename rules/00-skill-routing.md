# Skill Routing

## Skill Location

Skills are located in:

```txt
.agents/skills/
```

## Skill Discovery

When choosing a skill, inspect available metadata in this order:

1. `skill.json`
2. `SKILL.md`
3. `AGENT.md`
4. `README.md`

## Skill Selection

Use the smallest suitable skill for the task.

If the user explicitly names a skill, prefer that skill unless it is clearly incompatible.

If multiple skills are needed, coordinate them through files under `.aix/artifacts/`.

Do not assume skills can call each other directly.

## Skill Registry

If a registry exists, prefer it for discovery:

```txt
.agents/skills/registry.json
```

A registry entry should look like:

```json
{
  "name": "example-skill",
  "path": ".agents/skills/example-skill",
  "description": "short explanation of what this skill does",
  "entrypoints": ["SKILL.md", "README.md"],
  "inputs": [],
  "outputs": []
}
```

## Multi-Skill Coordination

For multi-skill work:

1. Use `planning-with-files` to create or update the task context.
2. Route each skill based on its purpose.
3. Write each skill's outputs under the active task folder inside `.aix/artifacts/`.
4. Use file-based handoff when one skill produces input for another.
5. Update task progress whenever scope, decisions, or outputs change.
