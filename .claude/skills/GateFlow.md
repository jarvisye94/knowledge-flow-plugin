# GateFlow

```yaml
document_type: knowledgeflow_full_pipeline
schema_version: "1.0"
name: GateFlow
display_name: Full KnowledgeFlow Delivery Pipeline
purpose: Execute a complete delivery chain serially, with context control, stage gates, and artifact archival.

controller:
  dependency: PipelineController
  execution_mode: strict_serial

constraints:
  - stages_must_execute_strictly_in_order
  - skipping_stages_forbidden
  - documents_before_implementation
  - plugin_artifacts_must_be_converted_or_synced_to_.knowledge/

stages:
  - id: stage_1
    name: requirement_clarification_and_deep_interrogation
    role_agent: Agent_Requirement
    adapter_command: /GrillMeWithDocs
    required_outputs:
      - .knowledge/04-iterations-notes/
      - .knowledge/07-role-collaboration/change-scope/
      - .knowledge/01-architecture-decisions/adr/
  - id: stage_2
    name: task_planning_and_dependency_decomposition
    role_agent: Agent_TaskSplit
    adapter_command: /PlanningWithFiles
    required_outputs:
      - .knowledge/03-tasks-planning/task-plans/
      - .knowledge/03-tasks-planning/findings/
      - .knowledge/07-role-collaboration/change-scope/
  - id: stage_3
    name: technical_solution_and_specification_definition
    role_agent: Agent_Design
    adapter_command: /OpenSpec
    required_outputs:
      - .knowledge/02-requirements-specs/proposals/
      - .knowledge/02-requirements-specs/feature-design/
      - .knowledge/02-requirements-specs/specs/
  - id: stage_4
    name: TDD_coding_and_test_implementation
    role_agent: Agent_Developer
    adapter_command: /SuperPowers
    required_outputs:
      - implementation_changes
      - tests_or_verification_cases
      - .knowledge/04-iterations-notes/
      - .knowledge/05-delivery-validation/
  - id: review_gate
    name: mandatory_independent_review
    role_agent: Agent_Review
  - id: stage_5
    name: build_packaging_and_full_verification
    role_agent: Agent_Tester
    required_outputs:
      - .knowledge/05-delivery-validation/
  - id: stage_6
    name: deployment_and_smoke_verification
    role_agent: Agent_Tester
    required_outputs:
      - .knowledge/05-delivery-validation/
  - id: stage_7
    name: iteration_retrospective_and_final_archival
    role_agent: PipelineController
    required_outputs:
      - .knowledge/06-retrospectives/
      - closure_report

knowledge_policy:
  final_artifact_root: .knowledge/
```
