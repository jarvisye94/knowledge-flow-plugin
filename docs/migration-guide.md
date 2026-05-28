# Migration Guide

## Adding KnowledgeFlow to an Existing Project

### Option 1: Install as a Claude Code Plugin

1. Copy the `.claude/` directory from KnowledgeFlow into your project root:
   ```bash
   cp -r knowledgeflow/.claude/ your-project/.claude/
   ```
2. Copy the plugin manifest:
   ```bash
   cp -r knowledgeflow/.claude-plugin/ your-project/.claude-plugin/
   ```
3. Initialize the `.knowledge/` directory from templates:
   ```bash
   cp -r knowledgeflow/templates/.knowledge/ your-project/.knowledge/
   ```
4. Edit `.knowledge/00-project-baseline/` files to reflect your project facts.

### Option 2: Manual Copy

1. Copy individual command files from `.claude/commands/kf/` to your project's `.claude/commands/kf/`.
2. Copy skill files from `.claude/skills/` to your project's `.claude/skills/`.
3. Copy `.knowledge/` templates and fill in your project details.

### Important Notes

- The `.knowledge/` directory is the final artifact root. All workflow outputs go there.
- Do **not** reuse private project business knowledge in any publicly shared KnowledgeFlow artifacts.
- Commands use the `kf:` namespace (`kf:build`, `kf:feat`, `kf:fix`).
- The PipelineController must be present for any workflow to run correctly.
