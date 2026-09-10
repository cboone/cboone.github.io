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

# Create new post (then set sections in front matter)
hugo new content posts/my-post.md
```

## Project Structure

```text
.
├── archetypes/          # Templates for new content
├── assets/css/          # Custom CSS overrides
├── config/_default/     # Hugo configuration (hugo.yml)
├── content/
│   ├── llms/            # LLM category listing (_index.md with section-taxonomy layout)
│   ├── posts/           # All posts (categorized via sections front matter)
│   ├── projects/        # Project pages
│   ├── reports/         # Report pages
│   └── tools/           # Tools category listing (_index.md with section-taxonomy layout)
├── layouts/             # Custom layout overrides
├── static/              # Static files (images, favicon, etc.)
└── go.mod               # Hugo module dependencies (includes PaperMod theme)
```

## Configuration

Main configuration is in `config/_default/hugo.yml`. Key sections:

- `menu.main` - Navigation menu items
- `params.profileMode` - Homepage profile settings
- `params.socialIcons` - Social media links

## Content

All posts live in `content/posts/` and are categorized via a custom `sections` taxonomy in the front matter:

```yaml
sections: ["llms"]    # or "tools", "projects", etc.
```

Category listing pages (e.g., `content/llms/_index.md`) use the `section-taxonomy` layout, which queries all posts matching the given `sections` value and displays them automatically.

- Posts go in `content/posts/` with front matter including `date`, `title`, `sections`, and optional `description`
- Projects go in `content/projects/` with similar front matter
- Static files (images, PDFs) go in `static/`

## Deployment

Push to `production` branch triggers GitHub Actions workflow that builds and deploys to GitHub Pages.

## Styling

When making changes that involve colors or styling, consult the style references:

- **Colors:** `static/styles/colors/index.html` (available at `/styles/colors/` on the live site) - documents all CSS custom properties including backgrounds, text colors, accents, borders, scrollbar colors, and notice colors for both light and dark modes
- **Typography:** `static/styles/typography/index.html` (available at `/styles/typography/` on the live site) - documents font families, type scale, font weights, line heights, and letter spacing

Always use the existing CSS variables rather than hardcoded values.
