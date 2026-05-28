# KnowledgeFlow 知识库索引模板

metadata:
  document_type: knowledge_index
  version: "1.0"
  source_scope: ".knowledge/"

## directory_responsibilities

| directory | responsibility |
|---|---|
| `00-project-baseline/` | 长期稳定基线、项目概览、规则、术语 |
| `01-architecture-decisions/` | 架构决策和 ADR |
| `02-requirements-specs/` | 需求、规格、验收标准 |
| `03-tasks-planning/` | 任务拆解、计划、依赖 |
| `04-iterations-notes/` | 迭代过程和澄清记录 |
| `05-delivery-validation/` | 测试、构建、验证证据 |
| `06-retrospectives/` | 复盘、根因、改进 |
| `07-role-collaboration/` | Agent 协作、角色日志、风险和范围 |

## writing_rules

- Prefer YAML, tables, lists, stable headings, and explicit fields.
- Separate facts, assumptions, decisions, risks, commands, and results.
- Do not store secrets, credentials, private customer data, or unrelated implementation dumps.
