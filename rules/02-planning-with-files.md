# Planning With Files

## Purpose

Use `planning-with-files` as the default mechanism for task state, progress tracking, decisions, and context preservation.

## Skill Location

The skill should live at:

```txt
.agents/skills/planning-with-files/
```

The upstream source is:

```txt
https://github.com/OthmanAdi/planning-with-files/tree/master/skills/planning-with-files
```

## Default Usage

Use this skill at the start of every non-trivial task.

Use it again whenever:

- task scope changes
- user adds or changes requirements
- a meaningful decision is made
- a new skill is activated
- an artifact is created that affects downstream work
- implementation direction changes
- progress should be resumable by another agent
- work is paused, handed off, or summarized

## Responsibility

`planning-with-files` owns:

- task status
- progress notes
- durable context
- decisions
- task summaries
- resumability

Other skills must not create competing task-status systems unless explicitly allowed.

## Artifact Location

All planning files must stay under:

```txt
.aix/artifacts/<yyyymmdd-hhmm-task-slug>/
```

The exact internal structure should follow the `planning-with-files` skill's own rules, as long as it stays within the artifact boundary.

## Minimum Behavior

When starting a task, create or update durable planning context that includes:

- user request
- current goal
- known constraints
- active skill or skills
- current status
- next action

When meaningful progress happens, update the durable planning context.
