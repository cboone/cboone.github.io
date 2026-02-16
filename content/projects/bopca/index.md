---
date: 2026-01-06
description: "Run AI agents safely in lightweight macOS virtual machines"
externalUrl: "https://github.com/cboone/bopca"
title: "Bopca"
---

Run [Claude Code](https://docs.anthropic.com/en/docs/claude-code) and other AI agents in lightweight virtual machines on Apple Silicon Macs. Built on Apple's [container](https://developer.apple.com/documentation/virtualization) framework for hardware-level isolation with near-native performance.

## Features

- **One-command setup**: `bopca` initializes a container, mounts your repository, and opens a tmux session
- **Filesystem mirroring**: Your workspace mounts at its actual host path with customizable read/write permissions
- **Parallel development**: Built on [workmux](https://github.com/raine/workmux) and tmux for working across multiple branches simultaneously
- **Hardware-level security**: Agents run in isolated Linux containers with controlled filesystem access

## Installation

```bash
brew install cboone/tap/bopca
```

## Requirements

- Apple Silicon processor
- macOS 26 Tahoe
- Claude Code or OpenCode API key

## See also

### [bopca.sh](https://bopca.sh)

Project homepage.

### [Claude Code](https://docs.anthropic.com/en/docs/claude-code)

Anthropic's official CLI for Claude.

### [workmux](https://github.com/raine/workmux)

Git worktrees and tmux windows for parallel development.
