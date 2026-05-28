# Usage Guide

## Commands

| Command | Workflow | When to Use |
|---------|----------|-------------|
| `/kf:build <requirement>` | KnowledgeFlow (full) | New projects, MVPs, major versions, cross-module requirements |
| `/kf:feat <feature>` | KnowledgeFlow-Lite (feat) | Ordinary feature iterations |
| `/kf:fix <bug>` | KnowledgeFlow-Lite (fix) | Bug fixes or very small changes |

## Workflow Stages

### Full Pipeline (`/kf:build`)

1. **Requirement clarification** — Deep interrogation of goals, scenarios, constraints, and risks.
2. **Task planning** — Decomposition, dependencies, milestones, and change scope.
3. **Technical specification** — Proposal, design, specs, acceptance criteria, and TDD cases.
4. **Implementation** — TDD coding, verification, and evidence collection.
5. **Build and verification** — Full regression and packaging checks.
6. **Deployment and smoke test** — Steps, environment, rollback, and smoke verification.
7. **Retrospective** — Lessons, improvements, and closure report.

The mandatory independent review gate runs after implementation and before build verification; it is a gate, not an extra numbered business stage.

### Feature Iteration (`/kf:feat`)

1. Lightweight requirement clarification.
2. Incremental specification update.
3. TDD implementation.
4. Mandatory review.
5. Quick verification.

### Bug Fix (`/kf:fix`)

1. Issue scenario clarification.
2. Skip full planning (minimal change-scope ledger only).
3. Systematic debugging + fix + regression safety.
4. Mandatory review.
5. Local verification.

## Knowledge Base Structure

All workflow artifacts are archived under `.knowledge/`:

```
.knowledge/
├── 00-project-baseline/
├── 01-architecture-decisions/
├── 02-requirements-specs/
├── 03-tasks-planning/
├── 04-iterations-notes/
├── 05-delivery-validation/
├── 06-retrospectives/
└── 07-role-collaboration/
```

## Key Rules

- Stages execute **serially** — no parallel stage execution.
- Each stage must pass its gate before the next stage begins.
- Code changes require a **change-scope ledger** before implementation.
- Plugin default paths (like `CONTEXT.md`, `task_plan.md`) are **not** final artifacts; content must be converted into `.knowledge/`.
- High-risk changes trigger a **manual gate** and require user confirmation.
