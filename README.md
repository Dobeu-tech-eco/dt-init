# DT Init

<img src=".claude-plugin/icon.png" alt="DT Init icon" width="112">

DT Init gives Claude Code a workflow for planning, building, reviewing, and shipping software changes. It records decisions and verification evidence as the work progresses, so you can resume a task or review a pull request with its context.

## For people

Install DT Init from the Claude plugin directory when listed, or install it directly in Claude Code.

```text
/plugin marketplace add Dobeu-tech-eco/dt-init
/plugin install dt-init@dt-init
/reload-plugins
```

- Start with `/dt-init:onboard` to orient yourself in a repository.
- Use `/dt-init:feature` to turn a request into a plan and `/dt-init:run` to build and verify an approved task.
- Use `/dt-init:ship` to prepare a reviewed pull request and its change receipt.
- Use `/dt-init:check-in` to resume work from the repository's saved state.

See the [command guide](COMMAND-GUIDE.md) for the catalog. The workflows use Claude Code tools and the repository's own checks. Git and an authenticated GitHub CLI are needed for pull request workflows.

The knowledge store is a local folder you choose; DT Init ships no server for it and needs none. See [Knowledge](skills/knowledge/SKILL.md). Report issues in the [DT Init repository](https://github.com/Dobeu-tech-eco/dt-init/issues).

## For agents

Use the instructions in `skills/` and the roles in `agents/`. Follow the repository's approval rules and use the receipt check in the [ship skill](skills/ship/SKILL.md). Enter remote credentials through your own MCP client configuration. Use `YOUR_API_KEY` in examples.

This repository publishes a one-way release export. Use `claude plugin validate --profile directory --strict .` to check the plugin locally. The directory's review runs separately.

[MIT License](LICENSE.txt)
