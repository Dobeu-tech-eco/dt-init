---
name: composio
description: "Explain Composio, check whether it is already connected in this Claude Code setup, and report which installed plugins, MCP servers and skills it would overlap. Report only: this skill never connects, installs, disables or removes anything. Use when the user asks about Composio or trimming overlapping tools."
disable-model-invocation: true
---

> Directory edition: Use Claude Code’s built-in tools only. Do not execute bundled scripts or hooks, do not install or download anything, and do not read tokens or credential files from the machine. Carry out the step with Read, Grep and Glob.

# Composio — overlap report

Composio is a third-party tools integration that gives agents one authenticated connection to many apps (GitHub, Slack, Gmail, Notion, Linear and more). DT Init does not connect, configure or change Composio, and it never changes the user's other plugins, MCP servers or skills. This skill only reports.

## 1. Account question
Ask exactly one yes/no question with AskUserQuestion: "Do you have a Composio account?"
- **No**: write one paragraph explaining what Composio is and that the user can sign up on Composio's own website if they want it. Then stop.
- **Yes**: continue.

## 2. What is already here (read-only)
Using Read, Grep and Glob only, report:
- Whether a Composio connection is already present in the user's own Claude Code configuration (a Composio plugin entry or MCP server entry the user added themselves). Do not add one, and do not ask the user to add one as part of this skill.
- The installed plugins, MCP servers and skills whose job Composio's published toolkit catalogue overlaps (for example a separate GitHub, Slack or Gmail integration). Present them as a list with the overlapping toolkit named for each.

## 3. Report
Give the user the overlap list and one recommendation: which overlaps are worth their attention and why. Any change — connecting Composio, or switching anything off — is the user's own action in their own settings, outside this skill. DT Init makes no change itself.

## Guardrails
- Report only. Never connect, install, disable, archive or delete anything.
- Never read, print, copy or write API keys or credential files.
- Memory stays in the knowledge store (`/dt-init:knowledge`); Composio is a tools integration only.
- Keep the reply under 200 words unless the user asks for detail.
