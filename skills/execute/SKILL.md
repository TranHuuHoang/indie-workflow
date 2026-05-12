---
name: execute
description: Implement one scoped indie-workflow task. Use when the user asks to build, fix, implement, refactor, wire up, continue, or make code changes after context or planning. Keeps work focused, follows repo conventions, and hands off to verify before completion.
---

# Execute

Implement one scoped task and stop before starting unrelated work.

## Active KB

Before implementation, resolve durable context from the active KB:

1. Read `~/.indie-workflow/config` and use `KB_PATH` when present.
2. If project instructions declare a project-specific KB/wiki/docs path, prefer that path.
3. If no active KB is configured, run `./setup`; setup prefers a home KB such as `~/Engineering-KB` and falls back to repo-local `kb/`.

## Workflow

1. Read project instructions and adjacent code before editing.
2. For ambiguous or risky work, confirm the current task, acceptance criteria, and likely verification. For clear small fixes, proceed.
3. Keep changes scoped to the requested outcome.
4. Prefer existing patterns and helpers over new abstractions.
5. Add or update tests when behavior changes and the project has a test pattern.
6. If an approved plan starts a new project, create the initial KB project files before or alongside implementation.
7. Hand off to `verify` before calling the work done.

## New Project Setup

When an approved plan includes new project context, create or update the initial files in the active KB:

```text
projects/{project-name}/
├── index.md
├── context.md
├── prd.md
└── lessons.md
```

For MOC-style KBs, use `02_Projects/{project-name}/` with the same files.

Use the approved plan and available KB templates for the initial content. Preserve existing files if they already exist; update only the missing or clearly stale sections needed to start the project.

Do not hand this initial project setup to `capture`. `capture` is for later updates after implementation, verification, or shipping produces durable lessons, decisions, or changed context.

## Constraints

- Do not silently expand scope.
- Do not perform destructive git operations unless explicitly requested.
- Do not overwrite user changes.
- Do not introduce new frameworks or process machinery unless the task requires it.
- Do not use sub-agents for routine edits. Let `verify` decide whether risky work needs a separate review pass.
