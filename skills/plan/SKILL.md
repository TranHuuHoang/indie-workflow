---
name: plan
description: Right-size planning for indie-workflow. Use when the user asks to scope a feature, break down work, create a plan, write a small spec, decide next steps, turn an idea into implementation tasks, or prepare work before coding without a heavyweight ticketing process.
---

# Plan

Plan only as much as the task risk requires.

## Workflow

1. Use `context` first when the task depends on existing project knowledge.
2. Clarify the problem before solution details when requirements are ambiguous.
3. Define success criteria and explicit non-goals for medium or larger work.
4. Identify the smallest useful next task.
5. List likely files or systems touched.
6. Name the verification commands or manual checks.
7. Save a short spec only when the work will span multiple sessions or people.

## Sizing

- **Tiny**: one clear fix. Use a 2-4 item checklist and proceed.
- **Small**: one feature slice. Write acceptance criteria and verification.
- **Medium**: multiple files or uncertain behavior. Write a short spec/checklist.
- **Large/risky**: auth, billing, data, migrations, public APIs, security, or broad architecture. Require explicit success criteria, risks, rollback/verification, and review.

## Output

Prefer concise checklists over formal tickets unless the project already uses a tracker.

For small tasks:

```text
Plan:
1. ...
2. ...
Verify:
- ...
```

For larger tasks, use `templates/project-spec.md` if present or create a compact markdown spec in the source of truth.

## Reference

Read `../../references/core-workflow.md` for the risk model and workflow boundaries.
