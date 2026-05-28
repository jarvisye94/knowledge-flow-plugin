# SuperPowers

```yaml
document_type: knowledgeflow_adapter
schema_version: "1.0"
name: SuperPowers
display_name: TDD Coding and Verification Adapter
purpose: Connect KnowledgeFlow implementation stages with disciplined TDD, debugging, review, and verification.

execution_flow:
  - read_specification_document
  - read_change_scope_ledger
  - follow_test_driven_development
  - use_systematic_debugging_for_failures_or_unknown_causes
  - record_development_log
  - run_related_tests_static_checks_and_build_when_applicable
  - archive_verification_evidence

artifact_rules:
  final_targets:
    development_record: .knowledge/04-iterations-notes/
    verification_record: .knowledge/05-delivery-validation/
    retrospective: .knowledge/06-retrospectives/
  required_verification_fields:
    - command
    - result
    - status
    - conclusion
```
