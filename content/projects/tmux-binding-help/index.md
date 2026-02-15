---
date: 2026-01-18
description: "Interactive binding help popup for tmux"
externalUrl: "https://github.com/cboone/tmux-binding-help"
title: "tmux-binding-help"
---

An interactive popup for tmux that displays all key bindings in an organized, searchable interface. Replaces the default `prefix + ?` binding list with collapsible sections, search, and mouse support.

## Features

- Bindings organized by type: Prefix, Root, Copy Mode (vi/emacs), and custom tables
- Mouse bindings separated from keyboard shortcuts
- Collapsible/expandable groups
- Case-sensitive search with highlight and auto-expand
- Mouse and keyboard navigation
- Requires tmux 3.2+, no external dependencies

## Installation

With [TPM Redux](https://github.com/tmux-plugins/tpm) (recommended):

```bash
set -g @plugin 'cboone/tmux-binding-help'
```

Then press `prefix + I` to install.

## Usage

Press `prefix + ?` to launch the help popup.

**Navigation**: `j` / `k`, arrow keys, `PgUp` / `PgDn`, `g` / `G` for top/bottom.

**Groups**: `Enter` or `Space` to toggle, `c` to collapse all, `e` to expand all.

**Search**: `/` to search, `n` / `N` for next/previous match.

## See also

### [TPM Redux](https://github.com/tmux-plugins/tpm)

A maintained fork of the Tmux Plugin Manager.
