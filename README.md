# indie-workflow

Lightweight AI development workflow for indie devs and small teams.

`indie-workflow` keeps the useful parts of structured AI engineering workflows without importing a heavyweight agent operating system. It is designed for side projects, solo builders, and small teams who want a repeatable loop for context, planning, implementation, verification, and lesson capture.

## Skills

- `context` - load the smallest relevant project/wiki context.
- `plan` - turn a goal into a right-sized checklist or spec.
- `execute` - implement one scoped task.
- `verify` - run deterministic checks and acceptance review.
- `capture` - save durable lessons and decisions back to the source of truth.

## Principles

- Keep the core workflow tool-agnostic.
- Use a wiki, markdown vault, repo docs, or personal KB as the source of truth.
- Use `AGENTS.md`, `CLAUDE.md`, or equivalent as the tool adapter.
- Plan only as much as task risk requires.
- Verify with deterministic checks before calling work done.
- Capture durable lessons, not every task update.

## Install

Install into both Codex and Claude Code:

```bash
./setup
```

Install one target:

```bash
./setup --codex
./setup --claude
```

Install skills and initialize a local markdown KB:

```bash
./setup --all --kb ~/Engineering-KB
```

Initialize only the KB:

```bash
./setup --kb ~/Engineering-KB
```

The setup script symlinks each skill into:

- Codex: `${CODEX_HOME:-~/.codex}/skills`
- Claude Code: `~/.claude/skills`

Setup is idempotent:

- If a skill symlink already points to this repo, it is left alone.
- If a skill symlink points somewhere stale, it is updated.
- If a real file or directory exists at the target path, setup refuses to overwrite it.

When `--kb` is provided, setup creates a lightweight source-of-truth structure:

```text
00_Inbox/
01_Maps/
02_Projects/
03_Evergreen/
04_Decisions/
09_Templates/
```

It writes only missing files, so it will not overwrite an existing KB note.

If the target already looks like this user's Engineering KB, with `01_Maps/MOC - Engineering Knowledge Base.md`, setup preserves that structure and adds only missing templates under `09_Templates/`.

## Use In A Project

1. Copy `templates/AGENTS.md` for Codex or `templates/CLAUDE.md` for Claude Code into the project root.
2. Fill in the source-of-truth path and project commands.
3. Ask the agent to use `context`, `plan`, `execute`, `verify`, or `capture` as needed.

## Not Goals

- Not a replacement for tests, linting, or typechecking.
- Not a mandatory ticketing system.
- Not a multi-agent framework.
- Not tied to one AI coding tool.
