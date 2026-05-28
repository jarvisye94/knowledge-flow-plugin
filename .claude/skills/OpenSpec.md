# OpenSpec

```yaml
document_type: knowledgeflow_adapter
schema_version: "1.0"
name: OpenSpec
display_name: Specification-Driven Technical Design Adapter
purpose: Convert task plans into proposal, design, specifications, acceptance criteria, and TDD cases.

execution_flow:
  - read_requirement_and_task_plan
  - produce_technical_proposal
  - produce_design
  - define_interfaces_fields_rules_and_exceptions
  - define_acceptance_criteria
  - define_TDD_cases
  - sync_effective_artifacts_to_knowledge_base

artifact_rules:
  final_targets:
    proposal: .knowledge/02-requirements-specs/proposals/
    feature_design: .knowledge/02-requirements-specs/feature-design/
    specs: .knowledge/02-requirements-specs/specs/
  required_spec_fields:
    - background
    - goal
    - scope
    - non_goals
    - interfaces
    - fields
    - business_rules
    - exception_scenarios
    - acceptance_criteria
    - tdd_cases
```
