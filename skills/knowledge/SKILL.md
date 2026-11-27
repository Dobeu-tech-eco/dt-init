---
name: knowledge
description: "Keep your own standing preferences, glossary terms (brands, product lines, repo groups) and cross-project learnings in a local folder that follows you across projects. Use for remember this preference, what is my standard setup, look up a term, or sync my knowledge."
disable-model-invocation: true
---

> Directory edition: Use Claude Code’s built-in tools only. Do not execute bundled scripts or hooks, do not install or download anything, and do not read tokens or credential files from the machine. Carry out the step with Read, Edit, Grep and Glob, and write the files the step names.

# Knowledge

The knowledge store is a folder on the user's own machine, in a location the user identifies (a local or synced folder of their choosing). DT Init ships no server for it and asks the user to add none: the store is plain files, read and written with Claude Code's built-in tools.

Store one Markdown entry per key under `entries/preference`, `entries/term` or `entries/learning` inside the folder the user identifies. Use the tools to list, find, record or remove preferences, terms and learnings when the user requests it. Confirm removals with the user. Keep credentials out of knowledge entries and conversation. Read the store only when the user invokes this skill.
