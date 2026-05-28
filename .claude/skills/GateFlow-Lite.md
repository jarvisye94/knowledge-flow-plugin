# GateFlow-Lite

```yaml
document_type: knowledgeflow_lite_pipeline
schema_version: "1.0"
name: GateFlow-Lite
display_name: Lightweight KnowledgeFlow Iteration Pipeline
purpose: Choose between feature and fix branches while preserving core quality gates.

controller:
  dependency: PipelineController
  execution_mode: branch_serial

branches:
  feat:
    display_name: Normal Feature Iteration
    stages:
      - id: feat_stage_1
        name: lightweight_requirement_clarification
        role_agent: Agent_Requirement
        required_outputs:
          - .knowledge/04-iterations-notes/
          - .knowledge/07-role-collaboration/change-scope/
      - id: feat_stage_2
        name: incremental_technical_spec_update
        role_agent: Agent_Design
        required_outputs:
          - .knowledge/02-requirements-specs/specs/
      - id: feat_stage_3
        name: TDD_coding_and_incremental_tests
        role_agent: Agent_Developer
        required_outputs:
          - implementation_changes
          - tests_or_verification_cases
          - .knowledge/04-iterations-notes/
          - .knowledge/05-delivery-validation/
      - id: review_gate
        name: mandatory_independent_review
        role_agent: Agent_Review
      - id: feat_stage_4
        name: quick_verification
        role_agent: Agent_Tester
        required_outputs:
          - .knowledge/05-delivery-validation/
  fix:
    display_name: Bug Fix or Tiny Change
    stages:
      - id: fix_stage_1
        name: issue_scenario_clarification
        role_agent: Agent_Requirement
        required_outputs:
          - .knowledge/04-iterations-notes/
      - id: fix_stage_2
        name: skip_full_planning_and_specification
        role_agent: PipelineController
        required_outputs:
          - .knowledge/07-role-collaboration/change-scope/
      - id: fix_stage_3
        name: issue_fix_and_regression_safety_test
        role_agent: Agent_Developer
        required_outputs:
          - implementation_changes
          - regression_test_or_reason
          - .knowledge/04-iterations-notes/
          - .knowledge/05-delivery-validation/
      - id: review_gate
        name: mandatory_independent_review
        role_agent: Agent_Review
      - id: fix_stage_4
        name: local_verification
        role_agent: Agent_Tester
        required_outputs:
          - .knowledge/05-delivery-validation/
          - .knowledge/06-retrospectives/

constraints:
  - update_knowledge_incrementally_only
  - do_not_generate_redundant_large_documents
  - do_not_trigger_cross_module_refactoring
  - plugin_artifacts_must_be_converted_or_synced_to_.knowledge/
```
