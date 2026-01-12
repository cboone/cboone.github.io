# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Personal website for Christopher Boone, built with Hugo and the PaperMod theme. Deployed to GitHub Pages at `https://cboone.github.io`.

## Tech Stack

- **Static site generator:** Hugo
- **Theme:** PaperMod (Git submodule in `themes/PaperMod/`)
- **Deployment:** GitHub Actions to GitHub Pages
- **Branch strategy:** `main` for development, `production` for deployment

## Common Commands

```bash
# Run local development server
hugo server

# Build site (outputs to public/)
hugo

# Create new note
hugo new notes/my-note.md

# Create new project
hugo new projects/my-project.md
```

## Project Structure

```
.
├── archetypes/          # Templates for new content
├── assets/css/          # Custom CSS overrides
├── content/
│   ├── notes/           # Blog posts and notes
│   └── projects/        # Project pages
├── layouts/             # Custom layout overrides
├── static/              # Static files (images, favicon, etc.)
├── themes/PaperMod/     # Theme (Git submodule)
└── config.yml           # Hugo configuration
```

## Configuration

Main configuration is in `config.yml`. Key sections:

- `menu.main` - Navigation menu items
- `params.profileMode` - Homepage profile settings
- `params.socialIcons` - Social media links

## Content

- Notes go in `content/notes/` with front matter including `date`, `title`, and optional `description`
- Projects go in `content/projects/` with similar front matter
- Static files (images, PDFs) go in `static/`

## Deployment

Push to `production` branch triggers GitHub Actions workflow that builds and deploys to GitHub Pages.
