# cboone.github.io

## Project Overview

Personal website for Christopher Boone, built with Hugo and the PaperMod theme, as updated by [Pascal Michaillat](https://pascalmichaillat.org)'s [hugo-website theme](https://github.com/pmichaillat/hugo-website). Deployed to GitHub Pages at `https://cboone.github.io`.

## Tech Stack

- **Static site generator:** Hugo
- **Theme:** PaperMod (Hugo Module, see `go.mod`)
- **Deployment:** GitHub Actions to GitHub Pages
- **Branch strategy:** `main` for development, `production` for deployment

## Common Commands

```bash
# Run local development server
hugo server

# Build site (outputs to public/)
hugo

# Create new LLM post
hugo new llms/my-post.md

# Create new math post
hugo new math/my-post.md

# Create new project
hugo new projects/my-project.md

# Create new tool post
hugo new tools/my-tool.md
```

## Project Structure

```text
.
├── archetypes/          # Templates for new content
├── assets/css/          # Custom CSS overrides
├── content/
│   ├── llms/            # LLM-related posts
│   ├── math/            # Math-related posts
│   ├── projects/        # Project pages
│   └── tools/           # Tools I use
├── layouts/             # Custom layout overrides
├── static/              # Static files (images, favicon, etc.)
├── go.mod               # Hugo module dependencies (includes PaperMod theme)
└── config.yml           # Hugo configuration
```

## Configuration

Main configuration is in `config.yml`. Key sections:

- `menu.main` - Navigation menu items
- `params.profileMode` - Homepage profile settings
- `params.socialIcons` - Social media links

## Content

- LLM posts go in `content/llms/` with front matter including `date`, `title`, and optional `description`
- Math posts go in `content/math/` with front matter including `date`, `title`, and optional `description`
- Projects go in `content/projects/` with similar front matter
- Tool posts go in `content/tools/` with similar front matter
- Static files (images, PDFs) go in `static/`

## Deployment

Push to `production` branch triggers GitHub Actions workflow that builds and deploys to GitHub Pages.

## Styling

When making changes that involve colors or styling, consult the color scheme reference at `static/colors/index.html` (available at `/colors/` on the live site). This documents all CSS custom properties including backgrounds, text colors, accents, borders, scrollbar colors, and notice colors for both light and dark modes. Always use the existing CSS variables rather than hardcoded color values.
