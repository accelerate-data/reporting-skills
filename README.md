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

Codex installs plugins through registered marketplaces. Register the marketplace repo or
marketplace checkout that contains `reporting-skills`; do not register this plugin source repo
directly as a marketplace root.

## Local development

```bash
claude --plugin-dir .      # Load without installing
claude plugin validate .   # Validate structure
python3 scripts/validate_plugin_manifests.py
python3 scripts/check_plugin_version_bump.py --base-ref origin/main
codex plugin marketplace --help  # Confirm the local Codex CLI marketplace workflow
```

## Updating the plugin

1. Make your changes to skills, commands, or rules
2. Bump `version` in both `.claude-plugin/plugin.json` and `.codex-plugin/plugin.json` to the same value
3. Validate: `python3 scripts/validate_plugin_manifests.py`
4. Check the shared version bump: `python3 scripts/check_plugin_version_bump.py --base-ref origin/main`
5. Validate in Claude: `claude plugin validate .`
6. Test locally in Claude: `claude --plugin-dir .`
7. Confirm the local Codex CLI marketplace workflow: `codex plugin marketplace --help`
8. Commit and push — the marketplaces pick up the latest default branch automatically
9. After merge, verify from the marketplace repo that references this plugin source
