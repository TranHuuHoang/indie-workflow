---
name: plan
description: Right-size planning for indie-workflow. Use when the user asks to scope a feature, break down work, create a plan, write a small spec, decide next steps, turn an idea into implementation tasks, or prepare work before coding without a heavyweight ticketing process.
---

# Plan

Plan only as much as the task risk requires.

## Active KB

Use the active KB for specs, constraints, and durable project context:

1. Read `~/.indie-workflow/config` and use `KB_PATH` when present.
2. If project instructions declare a project-specific KB/wiki/docs path, prefer that path.
3. If no active KB is configured, run `./setup`; setup prefers a home KB such as `~/Engineering-KB` and falls back to repo-local `kb/`.

## Workflow

1. Use `context` first when the task depends on existing project knowledge.
2. Clarify the problem before solution details when requirements are ambiguous.
3. Define success criteria and explicit non-goals for medium or larger work.
4. Identify the smallest useful next task.
5. List likely files or systems touched.
6. Name the verification commands or manual checks.
7. Save project context or a PRD in the active KB when the work starts a new project or will span multiple sessions.

## New Project Mode

When the user starts a new project, create or update a project folder in the active KB before implementation:

```text
projects/{project-name}/
├── index.md
├── context.md
├── prd.md
└── lessons.md
```

For MOC-style KBs, use `02_Projects/{project-name}/` with the same files.

Use `templates/project-context.md` and `templates/prd.md` from the active KB when present. Keep the PRD practical: problem, users, success criteria, scope, constraints, and first milestone.

## Sizing

- **Tiny**: one clear fix. Use a 2-4 item checklist and proceed.
- **Small**: one feature slice. Write acceptance criteria and verification.
- **Medium**: multiple files or uncertain behavior. Write a short spec/checklist.
- **Large/risky**: auth, billing, data, migrations, public APIs, security, or broad architecture. Require explicit success criteria, risks, rollback/verification, and review.

## Output

Prefer concise checklists over formal tickets unless the project already uses a tracker.

For small tasks:

```text
Plan:
1. ...
2. ...
Verify:
- ...
```

For larger feature slices inside an existing project, use `templates/project-spec.md` from the active KB if present, or create a compact markdown spec in that project's KB folder.
