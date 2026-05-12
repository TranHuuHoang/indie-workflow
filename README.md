# indie-workflow

Lightweight AI coding workflow for indie devs and small teams.

```text
context -> plan -> execute -> verify -> capture
```

## Setup

```bash
./setup
```

This installs all skills globally for Codex and Claude Code, then finds or creates an active KB.

Default KB behavior:

- prefers `~/Engineering-KB`
- otherwise finds one home-folder KB with `KB`, `kb`, `Knowledge`, or `knowledge` in the name
- otherwise reuses an existing `~/.indie-workflow/config` KB path
- otherwise uses repo-local `./kb`
- saves the chosen path to `~/.indie-workflow/config`

Use a specific KB:

```bash
./setup --kb ~/Engineering-KB
```

Install for one tool only:

```bash
./setup --codex
./setup --claude
```

## How To Use

After setup, the skills are available across projects.

Ask your AI assistant naturally:

```text
Use context and plan for this feature.
Execute the approved plan.
Verify the change.
Capture the durable lesson in the KB.
```

Optional project instructions:

- Codex: copy `templates/AGENTS.md` to your project root
- Claude Code: copy `templates/CLAUDE.md` to your project root

Only do this when the project needs its own commands, conventions, or KB/wiki/docs override.

## Skills

- `context` - reads the smallest useful project and KB context before work.
- `plan` - works with you to shape requirements, tradeoffs, scope, success criteria, and the next executable slice.
- `execute` - follows the approved plan and makes one scoped change.
- `verify` - runs tests, lint, build, smoke checks, and reviews done-ness.
- `capture` - saves later durable lessons, decisions, and context updates.

## How The KB Fits

The KB is the source of truth for durable project context, PRDs, decisions, lessons, and reusable engineering knowledge.

For a new lightweight KB, setup creates:

```text
index.md
inbox/
projects/
lessons/
decisions/
templates/
```

Project context lives in the project source of truth:

```text
projects/{project-name}/
├── index.md
├── context.md
├── prd.md
└── lessons.md
```

For MOC-style KBs, use:

```text
02_Projects/{project-name}/
```

If a project already has its own KB, wiki, or docs path, use that. Do not duplicate it into the global KB.

## Efficient Workflow

1. Describe the project, goal, constraints, and what already exists.
2. Use `context` to connect that description with the active KB or project source of truth.
3. Spend most of the time in `plan`: clarify requirements, tradeoffs, non-goals, phases, and success criteria with the user.
4. For a first-time project, let `plan` define the KB/project docs and `execute` create them after approval.
5. Use `execute` only after the plan is approved. It should follow the plan, not expand scope.
6. Use `verify` before calling the work done.
7. Use `capture` only for durable updates after work happens.

Most useful prompts:

```text
Here is the project I want to build: ...
Use context from the active KB, then plan this properly with me before coding.
Ask me about unclear requirements, tradeoffs, and scope boundaries.
Execute this plan exactly. If scope changes, stop and re-plan.
Verify with the repo commands and acceptance criteria.
Capture only durable lessons or decisions from this work.
```
