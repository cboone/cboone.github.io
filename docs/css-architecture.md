# CSS Architecture

This document describes the CSS architecture of the Hugo project, explaining how PaperMod theme styles interact with custom overrides.

## Theme Acquisition

- **Theme**: PaperMod, imported as a Hugo Module (not a Git submodule)
- **Source**: `github.com/adityatelange/hugo-PaperMod` (defined in `go.mod`)
- **Location**: Downloaded during build, not stored in repository
- **Configuration**: `config.yml` lines 5-7

## Custom CSS Organization

All custom styles are located in `assets/css/`:

```text
assets/css/
├── core/
│   └── theme-vars.css          # CSS variables (colors, spacing, typography)
├── common/                      # Overrides/extensions for common components
│   ├── 404.css                 # 404 page styles
│   ├── archive.css             # Archive page styles
│   ├── footer.css              # Footer styles
│   ├── header.css              # Navigation header styles
│   ├── main.css                # Main container and global layout
│   ├── post-entry.css          # Post listing/entry card styles
│   ├── post-single.css         # Single post page styles (largest file)
│   ├── profile-mode.css        # Homepage profile section styles
│   ├── search.css              # Search page styles
│   └── terms.css               # Tag/taxonomy page styles
└── extended/                    # Extensions (applied AFTER core)
    ├── notice.css              # Custom notice/alert box styling
    └── typography.css          # Custom font faces and typography
```

## CSS Processing and Bundling

The CSS loading pipeline is defined in `layouts/partials/head.html` (lines 35-71).

### Processing Chain

1. **Includes Bundle** (optional scroll-bar styles)
   - `css/includes/scroll-bar.css` (conditional)
   - Result: `assets/css/includes.css`

2. **Core Bundle** (theme base + overrides, minified)
   - `css/core/theme-vars.css` - CSS variables
   - `css/core/reset.css` - Theme reset styles
   - `css/common/*.css` - All custom common styles concatenated
   - `css/includes/chroma-styles.css` - Syntax highlighting
   - `css/includes/chroma-mod.css` - Syntax highlighting customizations
   - `css/includes.css` - Include bundle (from step 1)
   - `css/core/zmedia.css` - Media query utilities
   - Result: `assets/css/core.css` (minified)

3. **Extended Bundle** (custom extensions, minified)
   - `css/extended/*.css` - All extended styles concatenated
   - Result: `assets/css/extended.css` (minified)

4. **Final Stylesheet** (all bundles concatenated)
   - `css/core/license.css` - License information
   - `core.css` (from step 2)
   - `extended.css` (from step 3)
   - Result: `assets/css/stylesheet.css`
   - Fingerprinting: Hash added for cache-busting (enabled by default)
   - Integrity: SRI hash included in `<link>` tag for security

### Processing Order Summary

```text
Theme Base CSS (from PaperMod module)
  |
  v
Theme Reset & Core Variables (theme-vars.css)
  |
  v
Common Overrides (404, archive, footer, header, main, post-entry, post-single, profile-mode, search, terms)
  |
  v
Syntax Highlighting (chroma-styles.css, chroma-mod.css)
  |
  v
Extended Features (notice.css, typography.css)
  |
  v
Final stylesheet.css (minified + fingerprinted)
```

## Override Mechanism

- PaperMod theme styles come from the Hugo module (not visible in repository)
- Custom styles in `assets/css/` are processed **after** the theme base CSS
- The `extended/` directory styles are applied **last**, giving them highest specificity priority
- CSS variables defined in `theme-vars.css` are used throughout, enabling easy customization

## Key CSS Files

| File | Lines | Purpose |
|------|-------|---------|
| `theme-vars.css` | 67 | Root CSS variables for colors, spacing, typography scale (Major Third 1.25), line heights |
| `post-single.css` | 453 | Complete post page styling (headings, links, code blocks, tables, TOC, images, blockquotes) |
| `post-entry.css` | 109 | Post card/listing styles, first-entry featured post styles |
| `header.css` | 94 | Navigation bar, logo, theme toggle button, menu styling |
| `footer.css` | 60 | Footer and «back to top» button styles |
| `profile-mode.css` | 49 | Homepage profile section with avatar and action buttons |
| `main.css` | 77 | Main container width/padding, pagination, social icons |
| `notice.css` | 194 | Alert/notice boxes with 12 variants (note, warning, danger, etc.) and dark mode colors |
| `typography.css` | 56 | Public Sans font-face declarations (regular, italic, medium, semibold, bold) |
| `archive.css` | 48 | Archive/historical posts page layout |
| `search.css` | 36 | Search results styling |
| `terms.css` | 20 | Tag/taxonomy listing page styles |
| `404.css` | 13 | 404 error page styles |

## Dark Mode Support

- **Implementation**: `data-theme="dark"` attribute on `<html>` element
- **Variables**: Separate color values defined for `[data-theme="dark"]` in:
  - `theme-vars.css` (lines 48-58)
  - `notice.css` (lines 116-193)
  - `head.html` noscript fallback (lines 112-141)
- **Theme Toggle**: Theme preference detection script in `head.html` (lines 156-192)
- **Storage**: Uses localStorage for `pref-theme` preference
- **Fallback**: Respects `prefers-color-scheme: dark` media query for system preferences

## Configuration Details

From `config.yml`:

- **Fingerprinting**: Enabled by default (adds hash to stylesheet filename for cache-busting)
- **Scroll Bar Style**: Disabled (`disableScrollBarStyle: true`)
- **Theme Variables**: Customizable in `theme-vars.css` rather than config
- **Module Import**: Line 7 imports PaperMod module automatically during build

## Build Output

- Production builds generate: `/public/assets/css/stylesheet.[hash].css`
- Hashes change when CSS content changes
- Integrity attribute included for subresource integrity (SRI) validation
- Preload directive (`rel="preload"`) for fast stylesheet loading
