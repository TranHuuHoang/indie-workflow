# indie-workflow

Lightweight AI development workflow for indie devs and small teams.

`indie-workflow` keeps the useful parts of structured AI engineering workflows without importing a heavyweight agent operating system. It is designed for side projects, solo builders, and small teams who want a repeatable loop for context, planning, implementation, verification, and lesson capture.

## Skills

- `context` - load the smallest relevant project/wiki context.
- `plan` - turn a goal into a right-sized checklist or spec.
- `execute` - implement one scoped task.
- `verify` - run checks and review whether work is done.
- `capture` - save durable lessons and decisions back to the source of truth.

## Principles

- Keep the core workflow tool-agnostic.
- Use a wiki, markdown vault, repo docs, or personal KB as the source of truth.
- Use `AGENTS.md`, `CLAUDE.md`, or equivalent as the tool adapter.
- Plan only as much as task risk requires.
- Verify with deterministic checks before calling work done.
- Capture durable lessons, not every task update.

## Install

Default setup installs the skills into Codex and Claude Code, then creates or checks a repo-local KB at `./kb`:

```bash
./setup
```

`./kb` is ignored by git so your local notes are not committed to this workflow repo.

Use an existing external KB instead:

```bash
./setup --kb ~/Engineering-KB
```

The active KB path is saved to `~/.indie-workflow/config` so the skills can find it:

```bash
KB_PATH="/path/to/active/kb"
```

The setup script always initializes or checks the active KB. If the KB path exists, setup checks whether it aligns with the workflow and warns about missing pieces. If it does not exist, setup initializes it.

The setup script also symlinks each skill into:

- Codex: `${CODEX_HOME:-~/.codex}/skills`
- Claude Code: `~/.claude/skills`

Setup is idempotent:

- If a skill symlink already points to this repo, it is left alone.
- If a skill symlink points somewhere stale, it is updated.
- If a real file or directory exists at the target path, setup refuses to overwrite it.

Advanced: install skills for one target only while still checking the active KB:

```bash
./setup --codex
./setup --claude
```

Tool flags only narrow skill installation. Use `--kb PATH` in the same command when you want an external KB.

When `--kb` points to a new path, setup creates a lightweight source-of-truth structure:

```text
index.md
inbox/
projects/
lessons/
decisions/
templates/
```

When `--kb` points to an existing path, setup checks the structure and warns about missing alignment points. It does not modify existing KBs.

Project context belongs in the active KB too. For a new project, create:

```text
projects/{project-name}/
├── index.md
├── context.md
├── prd.md
└── lessons.md
```

Use `templates/project-context.md` and `templates/prd.md` as the starting point.

For existing MOC-style KBs, use the same files under `02_Projects/{project-name}/`.

## Use In A Project

1. Copy `templates/AGENTS.md` for Codex or `templates/CLAUDE.md` for Claude Code into the project root.
2. Fill in the project commands. Keep the active KB config, or add a project-specific KB override only when needed.
3. Ask the agent to use `context`, `plan`, `execute`, `verify`, or `capture` as needed.

See `templates/AGENTS.example.md` for a filled Codex example.

## Not Goals

- Not a replacement for tests, linting, or typechecking.
- Not a mandatory ticketing system.
- Not a multi-agent framework.
- Not tied to one AI coding tool.
