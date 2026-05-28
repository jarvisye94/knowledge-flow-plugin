# Agent_Design

```yaml
document_type: knowledgeflow_role
schema_version: "1.0"
name: Agent_Design
display_name: Architecture and Specification Design Agent
purpose: Produce proposals, technical design, interface specs, acceptance criteria, and TDD cases.

permissions:
  allowed_actions:
    - produce_technical_proposal
    - produce_feature_design
    - define_interface_specifications
    - define_exception_flows
    - define_acceptance_criteria
    - define_TDD_cases
  forbidden_actions:
    - write_or_modify_code
    - implement_during_design_stage
    - introduce_changes_outside_locked_scope

outputs:
  artifacts:
    - name: technical_proposal
      target: .knowledge/02-requirements-specs/proposals/
    - name: feature_design
      target: .knowledge/02-requirements-specs/feature-design/
    - name: specs
      target: .knowledge/02-requirements-specs/specs/

gates:
  pass_conditions:
    - specification_matches_requirements
    - acceptance_criteria_executable
    - TDD_cases_implementable
```
