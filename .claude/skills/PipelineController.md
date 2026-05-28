# PipelineController

```yaml
document_type: knowledgeflow_controller
schema_version: "1.0"
name: PipelineController
display_name: KnowledgeFlow Pipeline Controller
purpose: Control workflow order, role boundaries, manual gates, scope locking, risk interception, artifact conversion, and closure reporting.

hard_constraints:
  - pipeline_must_execute_serially
  - next_stage_forbidden_until_current_stage_gate_passes
  - all_code_changes_require_change_scope_ledger_before_implementation
  - files_outside_change_scope_ledger_are_readonly
  - high_risk_targets_require_risk_annotation_and_manual_confirmation
  - each_role_must_write_a_role_log_after_completion
  - plugin_artifacts_count_as_complete_only_after_conversion_or_sync_to_.knowledge

role_sequence:
  KnowledgeFlow:
    - Agent_Requirement
    - Agent_TaskSplit
    - Agent_Design
    - Agent_Developer
    - Agent_Review
    - Agent_Tester
  KnowledgeFlow-Lite.feat:
    - Agent_Requirement
    - Agent_Design
    - Agent_Developer
    - Agent_Review
    - Agent_Tester
  KnowledgeFlow-Lite.fix:
    - Agent_Requirement
    - Agent_Developer
    - Agent_Review
    - Agent_Tester

manual_gates:
  required_when:
    - user_confirmation_required_after_design_and_task_scope_are_locked_before_formal_coding
    - code_review_finds_high_risk_scope_risk_or_branch_constraint_violation
    - shared_component_modified
    - core_legacy_logic_modified
    - low_level_framework_modified
    - any_role_triggers_high_risk
  action: Pause the flow, write a risk log, and wait for manual approval.

protocols:
  role_log_protocol:
    target: .knowledge/07-role-collaboration/agent-logs/
    required_after_each_role: true
  change_scope_protocol:
    target: .knowledge/07-role-collaboration/change-scope/
    required_before_code_change: true
    required_fields:
      - modifiable_files
      - readonly_files
      - forbidden_modules
      - related_regression_scope
  plugin_artifact_conversion_protocol:
    final_source_of_truth: .knowledge/
    forbidden_final_paths:
      - CONTEXT.md
      - docs/adr/
      - task_plan.md
      - findings.md
      - progress.md
  stage_gate_output_protocol:
    schema:
      stage:
        name: string
        role: string
        adapter_skill: string
        official_skill: string
        input: list[string]
        output: list[string]
        knowledge_target: list[string]
        gate:
          artifacts_recorded_or_not_needed: boolean
          forbidden_paths_not_used: boolean
          role_boundary_respected: boolean
          current_stage_completed_before_next: boolean
        next_allowed: boolean
  closure_report_protocol:
    required_before_completion: true
```
