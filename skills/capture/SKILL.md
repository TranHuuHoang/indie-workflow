---
name: capture
description: Capture durable indie-workflow updates after work happens. Use when the user asks to remember, save, update the KB/wiki, capture findings, write lessons, document decisions, or preserve reusable knowledge after debugging, verification, or shipping. Initial project context and PRD creation after an approved plan belong to execute.
---

# Capture

Save durable updates back to the source of truth after work creates lessons, decisions, or changed context.

## Active KB

Always resolve the active KB before writing durable context:

1. Read `~/.indie-workflow/config` and use `KB_PATH` when present.
2. If project instructions declare a project-specific KB/wiki/docs path, prefer that path.
3. If no active KB is configured, run `./setup`; setup prefers a home KB such as `~/Engineering-KB` and falls back to repo-local `kb/`.
4. Write to the active KB, not to the code repo, unless the project explicitly stores docs in-repo.

## Workflow

1. Identify whether the finding or update is durable enough to save.
2. Choose the right destination: inbox, project note, decision, or lesson.
3. Distill the lesson. Do not paste raw transcripts or logs.
4. Preserve existing useful context when updating notes.
5. For MOC/Obsidian-style KBs, add or update useful `[[wikilinks]]`, hub maps, and `## Related` sections so durable notes do not become isolated.
6. Link back to source files, commits, issues, or project notes when helpful.
7. Avoid secrets, credentials, tokens, private keys, raw sensitive logs, and customer data.
8. If this is initial project setup immediately after an approved plan, use `execute` instead.

## Capture These

- Updates to project context, PRDs, and specs that future sessions need.
- Reusable engineering lessons.
- Architecture decisions and tradeoffs.
- Setup gotchas.
- Domain concepts.
- Debugging findings likely to recur.
- Project constraints future sessions need.

## Skip These

- One-off task status.
- Temporary TODOs.
- Large generated output.
- Implementation details already obvious from code.

For simple KBs, project notes belong in `projects/{project-name}`. For MOC-style KBs, project notes belong in `02_Projects/{project-name}`.
