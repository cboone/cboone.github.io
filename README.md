# cboone.github.io

Personal website built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

## Development

```bash
# Install Hugo (macOS)
brew install hugo

# Clone repository
git clone https://github.com/cboone/cboone.github.io.git

# Run local server
hugo server

# Create a new post (then set sections in front matter)
hugo new content posts/my-post.md
```

Site available at http://localhost:1313/

## Content

All posts live in `content/posts/` and are categorized via a custom `sections` taxonomy in the front matter:

```yaml
sections: ["llms"]    # or "tools", "projects", etc.
```

Category listing pages (e.g., `content/llms/_index.md`) use a `section-taxonomy` layout that automatically displays all posts matching their section.

## Style References

Visual references for CSS custom properties are available:

- **Colors:** `/styles/colors/` (or `static/styles/colors/index.html` locally) - backgrounds, text colors, accents, borders, scrollbar colors, and notice colors for both light and dark modes
- **Typography:** `/styles/typography/` (or `static/styles/typography/index.html` locally) - fonts, type scale, line heights, and letter spacing

## Deployment

Pushes to the `production` branch trigger automatic deployment via GitHub Actions.
