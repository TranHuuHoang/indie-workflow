# Core Workflow

`indie-workflow` separates durable knowledge from implementation and current status.

## Boundaries

- **Source of truth** owns durable knowledge: specs, decisions, system notes, lessons.
- **Tracker** owns current status only when a tracker exists.
- **Code repo** owns implementation, commands, and local conventions.

For solo projects, the tracker can be a markdown checklist, GitHub issue, or nothing at all.

## Loop

```text
context -> plan -> execute -> verify -> capture
```

## Risk Model

Low risk:

- One to three files.
- Local UI or isolated logic.
- Existing tests or easy manual verification.

Medium risk:

- Several files or one subsystem.
- New data flow, async behavior, or integration.
- Partial tests.

High risk:

- Auth, billing, payments, permissions, migrations, data integrity, public APIs, security, or broad architecture.
- Many files or unclear rollback path.

Use heavier planning and review only as risk increases.
