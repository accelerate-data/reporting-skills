# Reporting Skills Plugin

Shared plugin repository for internal reporting and decision-making skills used by Claude Code and Codex.

**Maintenance rule:** This file contains durable repository guidance, not volatile inventory.

## Instruction Hierarchy

1. `AGENTS.md` - canonical, cross-agent source of truth
2. Skill-local references under `skills/<skill>/references/`
3. `CLAUDE.md` - Claude-specific adapter and routing

## Repository Purpose

Single plugin-source repo for internal reporting skills.

- Root manifests: `.claude-plugin/plugin.json` and `.codex-plugin/plugin.json`
- Canonical skill content: `skills/`

## Skills

- `skills/create-one-pager/SKILL.md` - create Amazon-style one-pager documents
- `skills/debating-it-out/SKILL.md` - structured multi-agent debates for decision-making
- `skills/one-pager-prd/SKILL.md` - one-pager product requirement documents
- `skills/package-for-review/SKILL.md` - package research into review-ready documents

## Conventions

- Keep all skill directories under `skills/`.
- Keep `.claude-plugin/plugin.json` and `.codex-plugin/plugin.json` on the same plugin name and version.
- When plugin content or metadata changes, bump both manifest versions together and run `python3 scripts/validate_plugin_manifests.py`.
