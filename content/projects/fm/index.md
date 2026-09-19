---
date: 2026-01-27
description: "Safe Fastmail management tool for LLMs"
externalUrl: "https://github.com/cboone/fm"
title: "fm"
---

A command-line interface for [Fastmail](https://www.fastmail.com) email that enforces safety through structural limitations. Provides reading, searching, archiving, spam marking, and mailbox moves --- and nothing more.

## Safety by design

Rather than relying on user restraint, `fm` enforces safety structurally:

- Email composition is impossible (the EmailSubmission API is never called)
- Permanent deletion is prevented (`Email/set` destroy is disabled)
- Moving to Trash is explicitly refused

Designed for use with [Claude Code](https://docs.anthropic.com/en/docs/claude-code) and other AI agents, where the consequences of an accidental destructive action are high.

## Installation

```bash
brew install cboone/tap/fm
```

## Commands

**Read-only operations**: session verification, mailbox listing, email retrieval with thread context, full-text search with date and sender filtering.

**Triage operations**: archiving, spam marking, flagging, moving between mailboxes, marking as read. All modification commands support `--dry-run` preview.

Output defaults to JSON for structured consumption by LLMs, with a text alternative available.

## See also

### [Fastmail](https://www.fastmail.com)

Fast, private email hosting with full JMAP API support.

### [Claude Code](https://docs.anthropic.com/en/docs/claude-code)

Anthropic's official CLI for Claude.
