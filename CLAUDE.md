# cboone.github.io

## Project Overview

Personal website for Christopher Boone, built with Hugo. Originally based on the [PaperMod theme](https://github.com/adityatelange/hugo-PaperMod), as updated by [Pascal Michaillat](https://pascalmichaillat.org)'s [hugo-website theme](https://github.com/pmichaillat/hugo-website). Deployed to GitHub Pages at `https://cboone.github.io`.

## Tech Stack

- **Static site generator:** Hugo
- **Theme:** PaperMod (vendored in `layouts/`, `assets/`, and `i18n/`)
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
├── assets/
│   ├── css/             # Stylesheets (variables, base, components)
│   └── js/              # JavaScript (search functionality)
├── config/              # Hugo configuration (split by environment)
├── content/
│   ├── llms/            # LLM-related posts
│   ├── math/            # Math-related posts
│   ├── projects/        # Project pages
│   └── tools/           # Tools I use
├── i18n/                # Internationalization strings
├── layouts/             # Hugo templates (based on PaperMod)
├── LICENSES/            # Third-party licenses (PaperMod, Fuse.js)
├── static/              # Static files (images, favicon, etc.)
└── go.mod               # Hugo module definition
```

## Configuration

Main configuration is in `config/_default/hugo.yml` with environment-specific overrides in `config/development/` and `config/production/`. Key sections:

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

When making changes that involve colors or styling, consult the style references:

- **Colors:** `static/styles/colors/index.html` (available at `/styles/colors/` on the live site) - documents all CSS custom properties including backgrounds, text colors, accents, borders, scrollbar colors, and notice colors for both light and dark modes
- **Typography:** `static/styles/typography/index.html` (available at `/styles/typography/` on the live site) - documents font families, type scale, font weights, line heights, and letter spacing

Always use the existing CSS variables rather than hardcoded values.
