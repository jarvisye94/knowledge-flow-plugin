# Fictional SaaS Example

This example demonstrates KnowledgeFlow workflow execution and knowledge accumulation for a fictional SaaS project called **TaskPilot** — a lightweight task management service.

## Domain

TaskPilot manages projects, tasks, and team assignments. It has no relation to any real product or service.

## Workflow Demonstration

### kf:build — New Project

```
/kf:build Build TaskPilot MVP with project CRUD, task assignment, and basic reporting
```

Stages produce:

1. **Requirement clarification** → `.knowledge/04-iterations-notes/` captures goals, scenarios, constraints, and risks.
2. **Task planning** → `.knowledge/03-tasks-planning/` records decomposition, dependencies, and milestones.
3. **Technical specification** → `.knowledge/02-requirements-specs/` records proposal, design, specs, and TDD cases.
4. **Implementation** → Code and verification evidence archived under `.knowledge/05-delivery-validation/`.
5. **Build and verification** → Build and test results recorded.
6. **Deployment** → Steps, environment, rollback plan, and smoke test recorded.
7. **Retrospective** → `.knowledge/06-retrospectives/` captures lessons and closure.

### kf:feat — Feature Iteration

```
/kf:feat Add due-date reminders for overdue tasks
```

Lightweight stages produce incremental updates under `.knowledge/` without a full proposal cycle.

### kf:fix — Bug Fix

```
/kf:fix Task completion count shows zero for projects with completed tasks
```

Minimal stages produce a fix, regression test, and root cause record.

## Sample Knowledge Artifacts

See `examples/fictional-saas/.knowledge/` for a small set of staged artifacts from a fictional `/kf:build` run.
