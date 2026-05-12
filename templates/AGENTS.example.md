# Project Agent Instructions

## What This Is

NotiSage is a small Next.js app that turns noisy product updates into concise user-facing notifications.

## Workflow

Use `indie-workflow`:

- `context` before planning or coding when project knowledge matters.
- `plan` to right-size the next task.
- `execute` for one scoped implementation task.
- `verify` before calling work done.
- `capture` when a durable lesson, decision, or gotcha should be saved.

## Source Of Truth

Active KB config: `~/.indie-workflow/config`

Start here:

- `{active-kb}/index.md`

Use the source of truth for durable context, specs, decisions, and lessons. Keep code and implementation details in this repo.

Project notes:

- `{active-kb}/projects/notisage/context.md`
- `{active-kb}/projects/notisage/prd.md`
- `{active-kb}/projects/notisage/lessons.md`

## Package Manager And Commands

Package manager: `pnpm`

- Dev: `pnpm dev`
- Test: `pnpm test`
- Typecheck: `pnpm typecheck`
- Lint: `pnpm lint`
- Build: `pnpm build`

## Before Calling Work Done

Run focused tests for changed behavior. For UI or shared code changes, also run typecheck and lint.

## Conventions

- Keep components small and colocate feature-specific helpers.
- Prefer existing app routes and data-fetching patterns.
- Add tests for parsing, filtering, and notification formatting behavior.

## Gotchas

- Notification copy should be short enough to fit mobile push previews.

## What Not To Do

- Do not store secrets, tokens, or raw sensitive logs in the source of truth.
- Do not rewrite durable context without preserving useful existing information.
- Do not perform destructive git operations unless explicitly requested.
