# PlanningWithFiles

```yaml
document_type: knowledgeflow_adapter
schema_version: "1.0"
name: PlanningWithFiles
display_name: Task Planning and Stage Decomposition Adapter
purpose: Convert confirmed requirements into executable tasks, dependencies, milestones, and change scope ledgers.

execution_flow:
  - read_confirmed_requirements
  - split_modules_and_subtasks
  - define_execution_order
  - define_task_dependencies
  - define_delivery_milestones
  - write_task_plan
  - write_findings_when_needed
  - write_change_scope_ledger_when_code_or_artifact_changes_are_involved

artifact_rules:
  final_targets:
    task_plan: .knowledge/03-tasks-planning/task-plans/
    findings: .knowledge/03-tasks-planning/findings/
    change_scope: .knowledge/07-role-collaboration/change-scope/
  required_task_fields:
    - task_id
    - goal
    - input
    - output
    - dependencies
    - execution_order
    - acceptance_criteria
    - risks_or_blockers
```
