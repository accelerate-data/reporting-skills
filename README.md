# Reporting Skills

Internal decisions with structured debates, proposals, and research packaging.

## Skills

| Skill | Description |
|-------|-------------|
| `create-one-pager` | Create Amazon-style one-pager documents |
| `debating-it-out` | Structured multi-agent debates for decision-making |
| `one-pager-prd` | One-pager product requirement documents |
| `package-for-review` | Package research into review-ready documents |

## Install

```bash
claude plugin add accelerate-data/reporting-skills
```

## Local development

```bash
claude --plugin-dir .      # Load without installing
claude plugin validate .   # Validate structure
```

## Updating the plugin

1. Make your changes to skills, commands, or rules
2. Bump `version` in `.claude-plugin/plugin.json`
3. Validate: `claude plugin validate .`
4. Test locally: `claude --plugin-dir .`
5. Commit and push — the marketplace picks up the latest default branch automatically (no version field in marketplace entries)
