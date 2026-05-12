---
name: verify
description: Verify and review completed work for indie-workflow. Use when checking completed changes, running tests, typecheck, lint, build, smoke tests, acceptance criteria, UI rendering checks, reviewing a diff, or deciding whether a task is actually done.
---

# Verify

Never call implementation done until the relevant checks pass or any skipped checks are clearly explained.

## Active KB

Use the active KB when acceptance criteria, specs, or project constraints are needed:

1. Read `~/.indie-workflow/config` and use `KB_PATH` when present.
2. If project instructions declare a project-specific KB/wiki/docs path, prefer that path.
3. If neither exists, use the repo-local `kb/` created by `./setup`.

## Workflow

1. Read verification commands from `AGENTS.md`, `CLAUDE.md`, package scripts, or repo docs.
2. Run focused checks first when available.
3. Run broader checks when the change has wider blast radius.
4. Check each acceptance criterion with concrete evidence.
5. For UI work, inspect the rendered page when practical.
6. Review the changed work for correctness, scope, and risk.
7. Report checks run, pass/fail status, and residual risk.

## Common Check Order

1. Focused tests for changed behavior.
2. Typecheck.
3. Lint.
4. Build.
5. Manual smoke test or UI review.

Adapt to the project. Do not invent commands if the repo does not support them.

## Lightweight Review

- Correctness against the requested behavior.
- Scope control.
- Tests for changed behavior.
- Security and data safety where relevant.
- No debug logs, dead code, or accidental generated churn.

## Risk Guidance

- **Low risk**: self-review changed files against acceptance criteria.
- **Medium risk**: run broader checks and inspect affected flows manually.
- **High risk**: recommend a separate review pass or sub-agent for auth, payments, migrations, security, public APIs, or broad refactors.

## Output

```text
Verification:
- test: PASS (`...`)
- typecheck: PASS (`...`)
- lint: not run (reason)
- acceptance: met / partially met / not met
- review: PASS / ISSUES FOUND
- residual risk: ...
```
