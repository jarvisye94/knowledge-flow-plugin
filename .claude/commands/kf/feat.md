---
name: "KF: Feat"
description: "Run the KnowledgeFlow-Lite controller workflow for ordinary feature iterations"
category: Workflow
tags: [workflow, knowledgeflow-lite, feature, controller]
---

Start the KnowledgeFlow-Lite feature iteration controller mode.

Use this command for ordinary feature iterations. It selects the feature branch and preserves requirement clarification, incremental specification, TDD, review, and quick verification.

**Input**: The feature iteration description provided after `/kf:feat`, passed as `$ARGUMENTS`.

**Mode**

- **Workflow**: KnowledgeFlow-Lite
- **Branch**: feat
- **Controller**: `.claude/skills/PipelineController.md`
- **Final artifact root**: `.knowledge/`
- **Write mode**: incremental only

**Steps**

1. Enter controller mode.
2. Select the KnowledgeFlow-Lite feature branch.
3. Run clarification, incremental specification, TDD implementation, mandatory review, and quick verification serially.
4. Convert or sync plugin artifacts into `.knowledge/`.
5. Report every stage gate and closure report.

**Guardrails**

- Do not run full planning by default.
- Do not generate a full architecture proposal by default.
- Do not perform cross-module refactoring.
- Do not enter the next stage before the current gate is satisfied.
- Final artifacts must live under `.knowledge/`.
