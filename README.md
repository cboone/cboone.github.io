# cboone.github.io

Personal website built with [Hugo](https://gohugo.io/) and the [PaperMod](https://github.com/adityatelange/hugo-PaperMod) theme.

## Development

```bash
# Install Hugo (macOS)
brew install hugo

# Clone repository
git clone https://github.com/cboone/cboone.github.io.git

# Install dependencies (required for CSS processing)
npm install

# Run local server
hugo server
```

**Note:** This project uses Tailwind CSS v4 with PostCSS. The `npm install` step is required before running Hugo to ensure CSS is processed correctly. Requires Node.js 18 or later.

Site available at http://localhost:1313/

## Style References

Visual references for CSS custom properties are available:

- **Colors:** `/styles/colors/` (or `static/styles/colors/index.html` locally) - backgrounds, text colors, accents, borders, scrollbar colors, and notice colors for both light and dark modes
- **Typography:** `/styles/typography/` (or `static/styles/typography/index.html` locally) - fonts, type scale, line heights, and letter spacing

## Deployment

Pushes to the `production` branch trigger automatic deployment via GitHub Actions.
