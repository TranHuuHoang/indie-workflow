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

When `--kb` points to a new path, setup creates a lightweight source-of-truth structure:

```text
00_Inbox/
01_Maps/
02_Projects/
03_Evergreen/
04_Decisions/
09_Templates/
```

When `--kb` points to an existing path, setup checks the structure, warns about missing alignment points, and writes only missing templates. It does not overwrite existing notes.

## Use In A Project

1. Copy `templates/AGENTS.md` for Codex or `templates/CLAUDE.md` for Claude Code into the project root.
2. Fill in the source-of-truth path and project commands.
3. Ask the agent to use `context`, `plan`, `execute`, `verify`, or `capture` as needed.

## Not Goals

- Not a replacement for tests, linting, or typechecking.
- Not a mandatory ticketing system.
- Not a multi-agent framework.
- Not tied to one AI coding tool.
