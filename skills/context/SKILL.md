---
name: context
description: Load and update project context for indie-workflow. Use when the user asks to read, search, use, inspect, or update a project wiki, KB, Obsidian vault, markdown context repo, AGENTS.md, CLAUDE.md, docs folder, architecture notes, specs, decisions, or lessons before planning or coding.
---

# Context

Find the smallest useful context before planning or implementation.

## Workflow

1. Read the repo instruction file first: `AGENTS.md`, `CLAUDE.md`, or equivalent.
2. Locate the source of truth from labels such as `Knowledge base:`, `Context repo:`, `Wiki:`, or `Docs:`.
3. Start from the source-of-truth index or map, not from a full-text dump.
4. Read only the notes needed for the current task.
5. Cite exact file paths and headings when answering from context.
6. If updating context, preserve existing useful material and keep the update distilled.

## What To Load

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

## Reference

Read `../../references/source-of-truth.md` when setting up or changing the wiki/KB shape.
