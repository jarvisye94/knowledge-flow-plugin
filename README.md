# KnowledgeFlow

KnowledgeFlow is a Claude Code workflow plugin that turns delivery work into reusable project knowledge.

It combines:

- **workflow control** — serial stage gates, role boundaries, risk interception, and closure reporting
- **knowledge accumulation** — every meaningful artifact is archived under `.knowledge/`
- **delivery discipline** — clarification, planning, specification, TDD, review, verification, and retrospective

## Why KnowledgeFlow?

Many AI coding workflows produce transient chat context. KnowledgeFlow makes the workflow produce durable project memory: requirements, design decisions, task plans, verification evidence, and retrospectives.

## Commands

| Command | Use for | Output |
|---------|---------|--------|
| `/kf:build <requirement>` | New projects, MVPs, major versions, complete delivery chains | Full KnowledgeFlow pipeline |
| `/kf:feat <feature>` | Ordinary feature iteration | Lightweight incremental flow |
| `/kf:fix <bug>` | Bug fixes or tiny changes | Minimal diagnosis/fix/verification flow |

## Quick Start

1. Copy the plugin payload into your project:

   ```bash
   cp -r .claude .claude-plugin /path/to/your-project/
   ```

2. Initialize your knowledge base:

   ```bash
   cp -r templates/.knowledge /path/to/your-project/.knowledge
   ```

3. Fill the baseline templates in:

   ```text
   .knowledge/00-project-baseline/
   ```

4. Run a workflow:

   ```text
   /kf:build Build the first MVP for my project
   /kf:feat Add a new feature
   /kf:fix Fix a reproducible bug
   ```

## Repository Layout

```text
knowledgeflow/
├── .claude-plugin/
│   └── plugin.json
├── .claude/
│   ├── commands/kf/
│   │   ├── build.md
│   │   ├── feat.md
│   │   └── fix.md
│   └── skills/
├── templates/.knowledge/
├── examples/fictional-saas/
├── docs/
│   ├── migration-guide.md
│   └── usage.md
├── README.md
├── CHANGELOG.md
└── LICENSE
```

## Workflow Model

### Full Pipeline: `/kf:build`

1. Requirement clarification
2. Task planning and dependency decomposition
3. Technical specification
4. TDD implementation
5. Build, packaging, and verification
6. Deployment and smoke verification
7. Retrospective and closure

The mandatory independent review gate runs after implementation and before build verification; it is a gate, not an extra numbered business stage.

### Lite Feature Pipeline: `/kf:feat`

1. Lightweight requirement clarification
2. Incremental specification update
3. TDD implementation
4. Mandatory independent review
5. Quick verification

### Lite Fix Pipeline: `/kf:fix`

1. Reproduction and impact clarification
2. Minimal change-scope ledger
3. Systematic debugging and regression safety
4. Mandatory independent review
5. Local verification and retrospective note

## Knowledge Base

KnowledgeFlow uses `.knowledge/` as the final artifact root:

```text
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

The templates are intentionally empty and generic. They do not include private business knowledge.

## Example

See [`examples/fictional-saas`](examples/fictional-saas/) for a fictional TaskPilot example showing how workflow artifacts accumulate.

## Migration

See [`docs/migration-guide.md`](docs/migration-guide.md) to adopt KnowledgeFlow in an existing project.

## Verification Checklist

Before publishing your fork or release:

- Required plugin files exist.
- Commands use the `kf:` namespace.
- `.knowledge` templates are generic placeholders.
- Examples are fictional.
- No private project identifiers or business facts are present.
- README and docs explain install, usage, migration, and verification.

## Contributing

Contributions should preserve these rules:

- Keep workflow stages explicit and serial.
- Keep `.knowledge/` as the final artifact root.
- Do not add private business facts to templates or examples.
- Prefer structured, AI-parseable documents.

## License

MIT
