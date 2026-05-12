# Source Of Truth

Use any durable knowledge store:

- Obsidian vault.
- Markdown folder in git.
- Repo `docs/`.
- Notion or Confluence export.
- Personal engineering KB.

## Recommended Shape

```text
knowledge-base/
├── 00_Inbox/
├── 01_Maps/
├── 02_Projects/
├── 03_Evergreen/
├── 04_Decisions/
└── 09_Templates/
```

Maps route agents to the right note. They should stay small.

This shape mirrors the user's Engineering KB style while staying generic enough for indie projects. Existing KBs do not need to be migrated; the important part is having a clear map/index and a stable place for durable project notes, decisions, and evergreen lessons.

## Store

- Project specs that span sessions.
- Architecture decisions and tradeoffs.
- Domain notes.
- Recurring debugging lessons.
- Setup gotchas.
- Integration constraints.

## Do Not Store

- Secrets, tokens, keys, credentials.
- Raw sensitive logs.
- Every task status update.
- Large generated dumps.
- Code that belongs in the repo.

## Setup

Run:

```bash
./setup --kb ~/Engineering-KB
```

The setup script creates missing folders and starter map files without overwriting existing notes.
