---
date: 2026-01-28
description: "Black-box testing library for terminal user interfaces"
externalUrl: "https://github.com/cboone/crawler"
title: "Crawler"
---

A Go testing library for black-box testing of terminal user interfaces. Runs binaries inside tmux sessions, sends keystrokes, captures screen output, and validates results using the standard `testing.TB` interface.

## Features

- **Framework-agnostic**: Test any TUI binary --- bubbletea, tview, tcell, Python curses, Rust ratatui, raw ANSI programs
- **Standard Go testing**: First-class integration with `testing.TB`, subtests, table-driven tests, `t.Helper()`, `t.Cleanup()`
- **Deterministic polling**: Reliable waits with configurable timeouts
- **Golden-file snapshots**: Capture and compare screen state against reference files
- **Zero dependencies**: Only the Go standard library

## Installation

```go
go get github.com/cboone/crawler
```

Requires Go 1.24+, tmux 3.0+, and a Unix-like system.

## Usage

```go
term := crawler.Open(t, "./my-app",
    crawler.WithSize(120, 40),
    crawler.WithTimeout(10 * time.Second),
)

term.Type("hello")
term.Press(crawler.Enter)
term.WaitFor(crawler.Text("world"))
```

Built-in matchers include `Text`, `Regexp`, `Line`, `LineContains`, `Not`, `All`, `Any`, `Empty`, and `Cursor` position matching.

## See also

### [Scrut](https://github.com/facebookincubator/scrut)

A testing toolkit for CLI applications by Facebook, focused on output snapshot testing.

### [bubbletea](https://github.com/charmbracelet/bubbletea)

The Elm-inspired TUI framework for Go by Charm.
