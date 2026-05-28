---
name: "KF: Fix"
description: "Run the KnowledgeFlow-Lite controller workflow for bug fixes or very small changes"
category: Workflow
tags: [workflow, knowledgeflow-lite, bugfix, controller]
---

Start the KnowledgeFlow-Lite bug-fix controller mode.

Use this command for bug fixes or very small changes. It selects the fix branch and keeps the scope minimal while preserving diagnosis, change-scope control, regression safety, review, and verification.

**Input**: The bug or tiny change description provided after `/kf:fix`, passed as `$ARGUMENTS`.

**Mode**

- **Workflow**: KnowledgeFlow-Lite
- **Branch**: fix
- **Controller**: `.claude/skills/PipelineController.md`
- **Final artifact root**: `.knowledge/`
- **Write mode**: incremental only

**Steps**

1. Enter controller mode.
2. Select the KnowledgeFlow-Lite fix branch.
3. Clarify reproduction, observed failure, impact scope, expected result, and regression points.
4. Create a minimal change-scope ledger before any code change.
5. Prefer systematic debugging before fixing.
6. Add minimal regression protection or record why no test applies.
7. Convert or sync plugin artifacts into `.knowledge/`.
8. Report every stage gate and closure report.

**Guardrails**

- Do not expand requirements.
- Do not perform unnecessary refactoring.
- Do not modify files outside the change-scope ledger.
- Final artifacts must live under `.knowledge/`.
