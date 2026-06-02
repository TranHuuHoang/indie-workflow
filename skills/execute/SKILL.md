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
6. Follow the approved plan exactly; if scope changes, pause and re-plan.
7. If an approved plan starts a new project for the first time, establish where durable project context should live before or alongside implementation.
8. For later work on an existing project, implement the planned code changes and update project docs only when the plan or changed context requires it.
9. Hand off to `verify` before calling the work done.

## New Project Setup

When an approved plan starts a project for the first time, establish the project's source-of-truth location.

If a source-of-truth preference is not already recorded, ask the user once whether durable project docs should live in:

- the active/general KB, or
- project-local files in the repo.

Remember that choice for the project by recording it in the chosen project context/index, repo docs, or project instructions. Future `execute` turns should reuse that recorded preference instead of asking again.

If the chosen location requires filesystem approval, request it when needed. If the user explicitly skips or postpones project docs, note that decision in the repo-local plan or status context.

If the project has its own declared KB, wiki, docs path, or external source of truth, use that location and do not create a duplicate project folder in the global KB.

If no project-specific source of truth exists, use the active KB:

```text
projects/{project-name}/
├── index.md
├── context.md
├── prd.md
└── lessons.md
```

For MOC-style KBs, use `02_Projects/{project-name}/` with the same files.

Use the approved plan and available templates for the initial content. If the project folder or files already exist, do not recreate the scaffold. Update only the files and sections named by the approved plan, or sections made stale by the current change.

For later tasks in the same project, `execute` should mainly change code. Update `context.md`, `prd.md`, `index.md`, or `lessons.md` only when the approved plan calls for it or the implementation changes durable project context.

Do not hand this initial project setup to `capture`. `capture` is for later updates after implementation, verification, or shipping produces durable lessons, decisions, or changed context.

## Constraints

- Do not silently expand scope.
- Do not perform destructive git operations unless explicitly requested.
- Do not overwrite user changes.
- Do not introduce new frameworks or process machinery unless the task requires it.
- Do not use sub-agents for routine edits. Let `verify` decide whether risky work needs a separate review pass.
