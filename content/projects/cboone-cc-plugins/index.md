---
date: 2026-01-14
description: "Skills and hooks for Claude Code"
externalUrl: "https://github.com/cboone/agent-harness-plugins"
title: "Claude Code Plugins"
---

A collection of plugins for [Claude Code](https://docs.anthropic.com/en/docs/claude-code).

The marketplace was previously named `cboone-cc-plugins` and is now
[`agent-harness-plugins`](https://github.com/cboone/agent-harness-plugins). GitHub redirects the
old URL, but the old marketplace name no longer works in `plugin install` commands.

## Notify

**Type**: Hooks

Notifies you when Claude finishes a task or needs your attention. Uses macOS notifications to alert you.

Requires [`terminal-notifier`](https://github.com/julienXX/terminal-notifier). The easiest installation method is via [Homebrew](https://brew.sh):

```bash
brew install terminal-notifier
```

## Write Bash Scripts

**Type**: Skills / Commands (merged as of [Claude Code 2.1.3](https://github.com/anthropics/claude-code/blob/main/CHANGELOG.md#213))

Applies Bash style conventions when creating or editing shell scripts. Claude Code should automatically use it when creating, editing, or reviewing shell scripts.

You can trigger it directly via `/write-bash-scripts`.

The Bash style conventions are in [`BASH.md`](https://github.com/cboone/agent-harness-plugins/blob/main/plugins/write-bash-scripts/skills/write-bash-scripts/references/BASH.md).

## Installation

Install plugins from this repository using Claude Code. The simplest way is open the plugins manager via `/plugin`, then `tab` to `Marketplace`, and hit `enter` to `Add Marketplace`. Type `cboone/agent-harness-plugins`, then choose which plugins you would like to install.

Or you can run more direct commands, either from within `claude`:

```bash
/plugin marketplace add cboone/agent-harness-plugins

/plugin install notify@agent-harness-plugins
/plugin install write-bash-scripts@agent-harness-plugins
```

Or from the command line:

```bash
claude plugin marketplace add cboone/agent-harness-plugins

claude plugin install notify@agent-harness-plugins
claude plugin install write-bash-scripts@agent-harness-plugins
```

## See also

### [Claude Code](https://docs.anthropic.com/en/docs/claude-code)

Anthropic's official CLI for Claude.

### [terminal-notifier](https://github.com/julienXX/terminal-notifier)

Send macOS notifications from the command line.
