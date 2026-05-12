---
name: plan
description: Collaborative planning for indie-workflow. Use when the user asks to scope a project or feature, shape requirements, compare tradeoffs, break down work, write a small spec, decide next steps, turn an idea into implementation tasks, or prepare work before coding.
---

# Plan

Planning is the main thinking phase of the workflow. Spend enough time with the user to make the work clear before implementation starts.

## Active KB

Use the active KB for specs, constraints, and durable project context:

1. Read `~/.indie-workflow/config` and use `KB_PATH` when present.
2. If project instructions declare a project-specific KB/wiki/docs path, prefer that path.
3. If no active KB is configured, run `./setup`; setup prefers a home KB such as `~/Engineering-KB` and falls back to repo-local `kb/`.

## Workflow

1. Use `context` first when the task depends on existing project knowledge.
2. Restate the goal, current understanding, assumptions, and open questions.
3. Keep the user in the loop. Ask for decisions when requirements, tradeoffs, or scope boundaries are unclear.
4. Define success criteria, non-goals, constraints, and important tradeoffs.
5. Explore the solution shape before choosing the implementation slice.
6. Break the chosen direction into phases or milestones when useful.
7. Define the next executable slice only after the broader plan is clear.
8. List likely files, systems, data, UI states, edge cases, and risks.
9. Name the verification commands, smoke checks, or acceptance checks.
10. For first-time new projects, define the source-of-truth artifacts that `execute` should create after the plan is approved.
11. For existing projects, mention doc updates only when the planned work changes durable project context.

## New Project Mode

When the user starts a new project, plan the project folder and initial source-of-truth files, but do not write them during planning unless the user explicitly asks.

If project instructions already declare a project-specific KB, wiki, docs path, or external source of truth, use that location. Do not also create a duplicate project folder in the global KB.

When no project-specific source of truth exists, use the active KB:

```text
projects/{project-name}/
├── index.md
├── context.md
├── prd.md
└── lessons.md
```

For MOC-style KBs, use `02_Projects/{project-name}/` with the same files.

The plan should specify:

- the target source-of-truth path
- which files should be created or updated
- the initial contents or outline for `context.md` and `prd.md`
- product goals, users, constraints, and non-goals
- key tradeoffs and decisions that need user approval
- the first implementation slice
- verification for that first slice

Use `templates/project-context.md` and `templates/prd.md` from the active KB when present. Keep the PRD practical: problem, users, success criteria, scope, constraints, and first milestone.

After the user approves the plan, `execute` owns creating the initial project source-of-truth files only the first time. For later work, `execute` follows the approved plan, changes code, and updates existing project docs only when needed. `capture` is for later lessons and decisions after work happens.

## Sizing

- **Tiny**: one clear fix. Confirm the goal, write a 2-4 item checklist, and proceed.
- **Small**: one feature slice. Clarify behavior, acceptance criteria, edge cases, and verification.
- **Medium**: multiple files or uncertain behavior. Work with the user on a short spec, tradeoffs, phases, and verification.
- **Large/risky**: auth, billing, data, migrations, public APIs, security, or broad architecture. Require explicit goals, non-goals, risks, rollout/rollback, verification, and review.

## Output

Prefer clear working plans over formal tickets unless the project already uses a tracker. Do not rush to implementation while major requirements or tradeoffs are still unresolved.

For small tasks:

```text
Understanding:
- ...
Decisions needed:
- ...
Plan:
1. ...
2. ...
Verify:
- ...
```

For larger feature slices inside an existing project, use `templates/project-spec.md` from the active KB if present, or create a compact markdown spec in that project's source-of-truth folder.

Before handing off to `execute`, the user should have approved the plan or clearly asked to proceed.
