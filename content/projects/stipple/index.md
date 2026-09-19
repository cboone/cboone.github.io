---
date: 2026-01-24
description: "Braille graphics rendering library for Go"
externalUrl: "https://github.com/cboone/stipple"
title: "Stipple"
---

A braille graphics rendering library for Go, designed for terminal-based games and visualizations. Uses Unicode braille patterns (U+2800 to U+28FF) to achieve pixel-level resolution in the terminal --- each character encodes a 2x4 dot grid, giving an 80-column terminal 160 horizontal pixels.

## Installation

```go
go get github.com/cboone/stipple
```

## Planned features

- Pixel-level canvas control using braille patterns
- Line rendering via Bresenham algorithm
- Rectangle and circle drawing (outlined and filled)
- Optional ANSI color support at the cell level
- Zero external dependencies

## How it works

Unicode braille patterns encode a 2x4 dot grid per character. An 80-column, 24-row terminal can display 160x96 pixels --- an 8x resolution improvement over standard character-based graphics.

## See also

### [drawille](https://github.com/asciimoo/drawille)

The original braille drawing library for Python that popularized this technique.

### [bubbletea](https://github.com/charmbracelet/bubbletea)

The Elm-inspired TUI framework for Go. Stipple could serve as a rendering backend for bubbletea applications.
