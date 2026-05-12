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
3. If neither exists, use the repo-local `kb/` created by `./setup`.

## Workflow

1. Read project instructions and adjacent code before editing.
2. For ambiguous or risky work, confirm the current task, acceptance criteria, and likely verification. For clear small fixes, proceed.
3. Keep changes scoped to the requested outcome.
4. Prefer existing patterns and helpers over new abstractions.
5. Add or update tests when behavior changes and the project has a test pattern.
6. Hand off to `verify` before calling the work done.

## Constraints

- Do not silently expand scope.
- Do not perform destructive git operations unless explicitly requested.
- Do not overwrite user changes.
- Do not introduce new frameworks or process machinery unless the task requires it.
- Do not use sub-agents for routine edits. Let `verify` decide whether risky work needs a separate review pass.
