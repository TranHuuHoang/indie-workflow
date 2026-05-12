# indie-workflow

A lightweight AI coding workflow for indie devs and small teams.

`indie-workflow` gives you a simple loop for building side projects with AI:

```text
context -> plan -> execute -> verify -> capture
```

It is intentionally small. No agent operating system, no heavy ticketing ritual, no organization-grade process. Just enough structure to keep your AI assistant grounded in your project and your knowledge base.

## Project Idea

Most AI coding sessions fail for boring reasons:

- the assistant does not know the project context
- plans are either too vague or too heavy
- implementation drifts from the actual goal
- verification is skipped
- useful lessons disappear after the chat ends

`indie-workflow` solves that with five installable skills:

- `context` - read the smallest useful project and KB context
- `plan` - turn a goal into a right-sized checklist or spec
- `execute` - implement one scoped task
- `verify` - run checks and review whether the work is done
- `capture` - save durable lessons and decisions back to the KB

The workflow is tool-friendly, not tool-specific. It installs into Codex and Claude Code, while your KB stays the source of truth.

## Setup

Run setup from this repo:

```bash
./setup
```

By default, setup:

- installs all skills into Codex and Claude Code
- looks for a KB under your home folder, preferring `~/Engineering-KB`
- saves the active KB path to `~/.indie-workflow/config`
- checks the KB structure and warns if important pieces are missing
- creates repo-local `./kb` only when no home or configured KB is found

Use a specific KB:

```bash
./setup --kb ~/Engineering-KB
```

Install for only one tool:

```bash
./setup --codex
./setup --claude
```

Tool flags only narrow skill installation. Setup always checks or initializes the active KB because the workflow depends on it.

## What This Gives You

A repeatable way to work with AI without turning your side project into enterprise process:

1. Start a project with context in your KB.
2. Ask AI to read the context before planning.
3. Plan only enough for the risk of the task.
4. Execute one scoped change.
5. Verify with real commands and acceptance criteria.
6. Capture later durable lessons, decisions, and context updates.

Example:

```text
context: read project context, PRD, existing decisions
plan: define the next small feature and success criteria
execute: make the focused code change
verify: run tests, lint, build, or a smoke check
capture: save the lesson, decision, or context update that should survive this chat
```

## KB Structure

For a new lightweight KB, setup creates:

```text
index.md
inbox/
projects/
lessons/
decisions/
templates/
```

Project context belongs in the KB too:

```text
projects/{project-name}/
├── index.md
├── context.md
├── prd.md
└── lessons.md
```

For MOC-style KBs, use the same project files under:

```text
02_Projects/{project-name}/
```

Use the included KB templates:

- `templates/project-context.md`
- `templates/prd.md`
- `templates/project-spec.md`

## Project Instructions

After setup, the skills are already installed globally and can be used across projects.

Per-project instruction files are optional. Add one only when a project needs its own commands, conventions, or KB override:

- Codex: copy `templates/AGENTS.md` to the project root
- Claude Code: copy `templates/CLAUDE.md` to the project root

Then fill in the project commands and keep the active KB config unless that project needs a different source of truth.

See `templates/AGENTS.example.md` for a filled Codex example.
