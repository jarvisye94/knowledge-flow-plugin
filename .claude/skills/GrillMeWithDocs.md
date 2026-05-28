# GrillMeWithDocs

```yaml
document_type: knowledgeflow_adapter
schema_version: "1.0"
name: GrillMeWithDocs
display_name: Requirement Clarification Adapter
purpose: Connect KnowledgeFlow archival rules with rigorous requirement interrogation.

execution_flow:
  - clarify_business_goal
  - clarify_usage_scenarios
  - clarify_constraints
  - clarify_exception_flows
  - clarify_compatibility_requirements
  - identify_risks
  - separate_confirmed_facts_open_questions_and_inferences
  - write_requirement_clarification_record

artifact_rules:
  final_targets:
    requirement_notes: .knowledge/04-iterations-notes/
    change_scope: .knowledge/07-role-collaboration/change-scope/
    adr_inputs: .knowledge/01-architecture-decisions/adr/
  style:
    - prefer_structured_yaml_tables_lists_and_stable_headings
    - do_not_write_inferences_as_facts
    - avoid_narrative_process_logs
```
