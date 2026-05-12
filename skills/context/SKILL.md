---
name: context
description: Load project context for indie-workflow. Use when the user asks to read, search, use, inspect, or understand a project wiki, KB, Obsidian vault, markdown context repo, AGENTS.md, CLAUDE.md, docs folder, architecture notes, specs, decisions, or lessons before planning or coding. For writing durable notes, use capture.
---

# Context

Find the smallest useful context before planning or implementation. This is a read/routing skill; durable writes belong to `capture`.

## Active KB

Resolve the active KB before reading context:

1. Read `~/.indie-workflow/config` and use `KB_PATH` when present.
2. If project instructions declare `Knowledge base:`, `Context repo:`, `Wiki:`, or `Docs:`, prefer that path for this project.
3. If no active KB is configured, run `./setup`; setup prefers a home KB such as `~/Engineering-KB` and falls back to repo-local `kb/`.
4. Start from `index.md`. Also support existing KB maps such as `01_Maps/MOC - Knowledge Base.md` or `01_Maps/MOC - Engineering Knowledge Base.md`.

## Workflow

1. Read the repo instruction file first: `AGENTS.md`, `CLAUDE.md`, or equivalent.
2. Locate the source of truth using the Active KB rules above.
3. Start from the source-of-truth index or map, not from a full-text dump.
4. Read only the notes needed for the current task.
5. Cite exact file paths and headings when answering from context.
6. If the user asks to save or update durable context, switch to `capture`.

## What To Load

- Project index, project context, and PRD from the active KB when they exist.
- For simple KBs, project notes live under `projects/{project-name}`.
- For MOC-style KBs, project notes live under `02_Projects/{project-name}`.
- Relevant project specs.
- Architecture notes.
- Existing decisions and constraints.
- Lessons and gotchas related to the current task.
- Local commands and conventions from the code repo.

## What Not To Store

- Secrets, credentials, tokens, private keys.
- Raw sensitive logs.
- Large generated dumps.
- Short-lived task status.
- Implementation details that belong in code.
