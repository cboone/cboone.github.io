---
date: 2026-01-15
description: "Convert Unix man pages to well-typeset EPUB files"
externalUrl: "https://github.com/cboone/manny-pub"
title: "manny-pub"
---

A toolkit for converting Unix manual pages into properly formatted EPUB files. Combines semantic HTML generation from [mandoc](https://mandoc.bsd.lv/) with professional typography styling via [pandoc](https://pandoc.org/) and custom CSS.

## How it works

1. Generate semantic HTML from a man page using `mandoc`
2. Convert to EPUB using `pandoc` with a chosen stylesheet
3. Optionally embed fonts for full typographic control

## Stylesheets

Four variants address different use cases:

- **man-clean.css** --- Minimal styling for validation
- **latex-libertinus.css** --- Professional typography with [Libertinus](https://github.com/alerque/libertinus) fonts
- **man-latex-bookerly.css** --- Optimized for Kindle
- **man-latex-libertinus.css** --- Full control with custom typefaces

The stylesheets recognize semantic markup from `mandoc`, applying appropriate treatment to command names, arguments, flags, file paths, and section headers.

## Requirements

```bash
brew install mandoc pandoc
```

## Why mandoc?

`mandoc` produces cleaner semantic HTML than `groff`, preserving inline element distinctions that `pandoc`'s native man reader would lose.

## See also

### [mandoc](https://mandoc.bsd.lv/)

A suite of tools for compiling man pages, producing clean semantic HTML output.

### [pandoc](https://pandoc.org/)

A universal document converter.

### [Libertinus fonts](https://github.com/alerque/libertinus)

A fork of Linux Libertine/Biolinum, used in the latex-libertinus stylesheet.

### [LaTeX.css](https://latex.vercel.app/)

Vincent Dorig's stylesheet that makes web content look like a LaTeX document, adapted for the EPUB stylesheets.
