---
name: machine-prep
description: "Audit this computer's agent tooling (plugins, agents, skills, MCP servers) against the blueprint profile and report what is enabled, what it costs in context, and where duplicates exist. Report only: this skill never disables, uninstalls or changes any plugin or setting. Use to review plugins or audit context budget."
disable-model-invocation: true
---

> Directory edition: Use Claude Code’s built-in tools only. Do not execute bundled scripts or hooks, do not install or download anything, and do not read tokens or credential files from the machine. Carry out the step with Read, Grep and Glob.

# Machine prep — audit and report

This skill audits the machine-level context budget: which plugins, agents, skills and MCP servers are enabled, where they come from, and what they cost. It reports findings and recommendations only. It never disables, uninstalls, moves or edits any plugin, skill, server or settings file — any change is the user's own action in their own settings, outside this skill.

The comparison profile defaults to the plugin's `profiles/blueprint.json`. A `profile` value in `.claude/dts2-harness.local.md` overrides it.

## 1. Inventory (read-only)
With Read, Grep and Glob, inventory:
- Enabled plugins in the user's settings and each plugin's source (marketplace, claude.ai sync, or project settings).
- Agent files in the user's agents folder, and agents that arrive inside enabled plugins, counted separately.
- Installed skills, including any that sync from the user's account.
- MCP servers the user has configured.
- Any duplicate plugins, skills, agents or MCP servers (same capability arriving from two sources).

## 2. Explain the sources
Report where the enabled set comes from, because that is what the user needs to act on themselves:
- Plugins enabled on the user's claude.ai account sync into Claude Code at session start and load enabled.
- Plugins a plugin or organisation marks required can only be changed by that organisation's admin.
- A project's own settings can enable plugins for that project, overriding the user-level setting.
- The blueprint's keep-set (`requiredByHarness` patterns in the profile, plus any `plugins:` list in a project's `.harness/keep.yaml`) names the plugins the harness's own skills depend on; flag these as keep in the report.

## 3. Report
Show: enabled plugins vs the keep-set, the largest context costs by source, duplicates (as information only — which copy to keep is the user's call), and anything in the keep-set that is missing. Recommend, in plain terms, what the user might switch off in their own settings and what each change would save. Then stop. Applying any of it is the user's own step, outside this skill.

## Guardrails
- Report only. Never disable, uninstall, move or edit anything.
- Never edit `.claude.json`, `auth.json`, or any credential file.
- Never write API keys.
