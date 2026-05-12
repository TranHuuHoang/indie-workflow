---
name: verify
description: Deterministic verification for indie-workflow. Use when checking completed changes, running tests, typecheck, lint, build, smoke tests, acceptance criteria, UI rendering checks, or reviewing whether a task is actually done.
---

# Verify

Never call implementation done until the relevant checks pass or any skipped checks are clearly explained.

## Workflow

1. Read verification commands from `AGENTS.md`, `CLAUDE.md`, package scripts, or repo docs.
2. Run focused checks first when available.
3. Run broader checks when the change has wider blast radius.
4. Check each acceptance criterion with concrete evidence.
5. For UI work, inspect the rendered page when practical.
6. Report checks run, pass/fail status, and residual risk.

## Common Check Order

1. Focused tests for changed behavior.
2. Typecheck.
3. Lint.
4. Build.
5. Manual smoke test or UI review.

Adapt to the project. Do not invent commands if the repo does not support them.

## Review Heuristics

- Correctness against the requested behavior.
- Scope control.
- Tests for changed behavior.
- Security and data safety where relevant.
- No debug logs, dead code, or accidental generated churn.

## Output

```text
Verification:
- test: PASS (`...`)
- typecheck: PASS (`...`)
- lint: not run (reason)
- acceptance: met / partially met / not met
```
