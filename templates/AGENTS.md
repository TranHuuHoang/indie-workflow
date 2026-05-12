# Project Agent Instructions

## What This Is

Describe the product or repo in one short paragraph.

## Workflow

Use `indie-workflow`:

- `context` before planning or coding when project knowledge matters.
- `plan` to right-size the next task.
- `execute` for one scoped implementation task.
- `verify` before calling work done.
- `capture` when a durable lesson, decision, or gotcha should be saved.

## Source Of Truth

Active KB config: `~/.indie-workflow/config`

Use the `KB_PATH` saved there unless this project needs its own KB.

Optional project-specific override. Delete this line if unused:

Knowledge base: `{optional-project-specific-kb-path}`

Start here:

- `{active-kb}/index.md`, or the existing KB map if this project uses a different KB structure.

Use the source of truth for durable context, specs, decisions, and lessons. Keep code and implementation details in this repo.

For first-time new projects, use `plan` to define the project context files, then `execute` to create the initial approved files:

- Simple KB: `{active-kb}/projects/{project-name}/context.md`, `prd.md`, and `lessons.md`
- MOC-style KB: `{active-kb}/02_Projects/{project-name}/context.md`, `prd.md`, and `lessons.md`

Use `capture` later for updates, lessons, and decisions after work happens.

## Package Manager And Commands

Package manager: `{npm | pnpm | yarn | uv | cargo | go | etc.}`

- Dev: `{command}`
- Test: `{command}`
- Typecheck: `{command}`
- Lint: `{command}`
- Build: `{command}`

## Before Calling Work Done

Run the relevant checks for the files changed. For larger changes, run the full test/typecheck/lint/build sequence.

## Conventions

- Match existing patterns before introducing new ones.
- Keep changes scoped to the requested task.
- Prefer small, reversible changes.
- Add tests when behavior changes or regression risk is meaningful.

## Gotchas

- `{non-obvious local setup or architecture detail}`

## What Not To Do

- Do not store secrets, tokens, or raw sensitive logs in the source of truth.
- Do not rewrite durable context without preserving useful existing information.
- Do not perform destructive git operations unless explicitly requested.
