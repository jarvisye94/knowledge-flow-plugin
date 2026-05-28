---
name: "KF: Build"
description: "Run the full KnowledgeFlow controller workflow for new projects, MVPs, major versions, or complete delivery chains"
category: Workflow
tags: [workflow, knowledgeflow, full, controller]
---

Start the full KnowledgeFlow controller mode.

Use this command for new projects, MVPs, major versions, or requirements that need the complete delivery chain. This command must enter PipelineController controller mode instead of only reading workflow files and stopping.

**Input**: The requirement description provided after `/kf:build`, passed as `$ARGUMENTS`.

**Mode**

- **Workflow**: KnowledgeFlow
- **Branch**: full
- **Controller**: `.claude/skills/PipelineController.md`
- **Final artifact root**: `.knowledge/`

**Required Reads**

Always read before stage execution:

- `.claude/skills/PipelineController.md`
- `.claude/skills/GateFlow.md`

Read only for stage 1:

- `.claude/skills/GrillMeWithDocs.md`
- `.claude/skills/Agent_Requirement.md`

Read later by stage when needed:

- `.claude/skills/PlanningWithFiles.md`
- `.claude/skills/OpenSpec.md`
- `.claude/skills/SuperPowers.md`
- `.claude/skills/Agent_TaskSplit.md`
- `.claude/skills/Agent_Design.md`
- `.claude/skills/Agent_Developer.md`
- `.claude/skills/Agent_Review.md`
- `.claude/skills/Agent_Tester.md`

**Steps**

1. Enter `.claude/skills/PipelineController.md` as the workflow controller.
2. Follow `.claude/skills/GateFlow.md` as the complete 7-stage workflow.
3. Execute each stage in order and do not enter the next stage until the current stage gate is satisfied.
4. Use the corresponding stage agent files when each stage requires role-specific instructions.
5. Convert or sync official/plugin artifacts into the corresponding `.knowledge/` directory.
6. At the end of every stage, output `PipelineController.protocols.stage_gate_output_protocol`.
7. Before finishing, output `PipelineController.protocols.closure_report_protocol`.

**Guardrails**

- Final artifacts must live under `.knowledge/`.
- Plugin default paths must not be treated as final project artifacts.
- Code changes require a change-scope ledger before implementation.
- High-risk or unclear scope requires a pause and manual confirmation.

**Output During Workflow**

```text
## Stage Gate Report

<content following PipelineController.protocols.stage_gate_output_protocol>
```

**Output On Completion**

```text
## Full KnowledgeFlow Closure Report

<content following PipelineController.protocols.closure_report_protocol>
```
