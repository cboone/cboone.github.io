---
date: 2026-02-15
description: "Nine new project pages, from AI agent sandboxing to braille rendering"
title: "New Projects"
---

I added nine new [project pages](/projects/) to the site, covering tools and libraries I've been building recently. Most are written in Go, several are designed for use with AI agents, and a few orbit the Alabaster color theme ecosystem.

## AI agent tooling

[**Bopca**](/projects/bopca/) runs Claude Code and other AI agents in lightweight virtual machines on Apple Silicon Macs. It uses Apple's container framework for hardware-level isolation with near-native performance. One command to initialize a container, mount your repo, and start working. This is the project I've been most focused on lately.

[**fm**](/projects/fm/) is a safe Fastmail management tool built specifically for LLMs. The key design decision: safety is structural, not behavioral. Email composition, permanent deletion, and trashing are all impossible --- the relevant API calls simply don't exist in the codebase. Claude Code can triage your email without the risk of an accidental send or delete.

[**Claude Code Plugins**](/projects/cboone-cc-plugins/) was already on the site, but worth mentioning here alongside the other agent tooling. It includes a macOS notification hook and a shell scripting style guide for Claude Code.

## Terminal tools

[**right-round**](/projects/right-round/) is a TUI for exploring 497 terminal progress indicators --- 378 spinners and 119 progress bars --- drawn from 26 open-source collections. Browse, preview animations, search, and export entries as JSON.

[**gh-problemas**](/projects/gh-problemas/) is a terminal UI for triaging GitHub issues, built as a `gh` CLI extension.

[**tmux-binding-help**](/projects/tmux-binding-help/) replaces tmux's default `prefix + ?` binding list with an interactive popup: collapsible groups, search with highlighting, mouse support.

## Go libraries

[**Crawler**](/projects/crawler/) is a black-box testing library for terminal user interfaces. It runs any TUI binary inside a tmux session, sends keystrokes, captures screen output, and validates results using the standard `testing.TB` interface. Works with bubbletea, tview, tcell, Python curses, Rust ratatui --- anything that writes to a terminal.

[**Attest**](/projects/attest/) provides type-safe assertion functions for Go tests, including golden file comparison. Smaller and more opinionated than testify.

[**Stipple**](/projects/stipple/) is a braille graphics rendering library. Unicode braille patterns encode a 2x4 dot grid per character, giving an 80-column terminal an effective resolution of 160x96 pixels. This one is still early --- functional but not yet feature-complete.

## Alabaster themes

[**Alabaster Themes Comparison**](/projects/alabaster-themes-comparison/) is a comprehensive catalog of every Alabaster color theme implementation I could find, spanning 15+ editors, IDEs, terminals, and other tools. It complements the [Alabaster Themes for Terminals](/projects/alabaster-themes-for-terminals/) project, which provides my own terminal color themes for 14 emulators.

## What's not here

I have a number of repos that are still too early to feature: tmux-theme-alabaster, tmux-package-status, vscode-theme-yet-another-alabaster, and several others that are either just getting started or are personal configuration that wouldn't be useful to anyone else. They'll get project pages when they're ready.
