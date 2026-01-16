# CSS Architecture

This document describes the CSS architecture of the Hugo project. All CSS is stored locally in the repository for complete control over styling.

## Theme Relationship

- **Theme**: PaperMod, imported as a Hugo Module (defined in `go.mod`)
- **CSS**: Fully extracted to local `assets/css/` directory
- **Layouts/i18n**: Still provided by the PaperMod module

The PaperMod module provides layouts, templates, and internationalization files, but all CSS has been extracted to the local repository for complete style control.

## CSS Organization

All styles are located in `assets/css/`:

```text
assets/css/
├── core/                        # Foundation styles
│   ├── license.css             # PaperMod license header
│   ├── reset.css               # CSS reset and base element styles
│   ├── theme-vars.css          # CSS variables (colors, spacing, typography)
│   └── zmedia.css              # Responsive media queries
├── common/                      # Component styles
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
├── includes/                    # Optional/conditional styles
│   ├── chroma-mod.css          # Syntax highlighting adjustments
│   ├── chroma-styles.css       # Chroma syntax theme (Catppuccin Macchiato)
│   └── scroll-bar.css          # Custom scrollbar styling
└── extended/                    # Extensions (applied last)
    ├── notice.css              # Alert/notice box styling
    └── typography.css          # Custom font faces (Public Sans)
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
License Header (license.css)
  |
  v
Core Variables (theme-vars.css)
  |
  v
CSS Reset (reset.css)
  |
  v
Component Styles (common/*.css)
  |
  v
Syntax Highlighting (chroma-styles.css, chroma-mod.css)
  |
  v
Scrollbar Styles (scroll-bar.css, if enabled)
  |
  v
Media Queries (zmedia.css)
  |
  v
Extended Styles (extended/*.css)
  |
  v
Final stylesheet.css (minified + fingerprinted)
```

## Customization

- All CSS is local and can be modified directly
- CSS variables in `theme-vars.css` control colors, spacing, and typography globally
- The `extended/` directory styles are applied last, useful for additions that need highest priority
- Component styles in `common/` can be edited individually without affecting other components

## Key CSS Files

### Core

| File                | Purpose                                                                 |
| ------------------- | ----------------------------------------------------------------------- |
| `license.css`       | PaperMod license header (MIT)                                           |
| `reset.css`         | CSS reset, base element styles, box-sizing, font defaults               |
| `theme-vars.css`    | CSS variables for colors, spacing, typography scale (Major Third 1.25)  |
| `zmedia.css`        | Responsive breakpoints and reduced-motion preferences                   |

### Common (Components)

| File                | Purpose                                                                 |
| ------------------- | ----------------------------------------------------------------------- |
| `post-single.css`   | Single post page (headings, links, code blocks, tables, TOC, images)    |
| `post-entry.css`    | Post cards/listing, first-entry featured post                           |
| `header.css`        | Navigation bar, logo, theme toggle, menu                                |
| `footer.css`        | Footer and «back to top» button                                         |
| `main.css`          | Main container width/padding, pagination, social icons                  |
| `profile-mode.css`  | Homepage profile section with avatar and action buttons                 |
| `archive.css`       | Archive/historical posts page layout                                    |
| `search.css`        | Search results styling                                                  |
| `terms.css`         | Tag/taxonomy listing page                                               |
| `404.css`           | 404 error page                                                          |

### Includes

| File                | Purpose                                                                 |
| ------------------- | ----------------------------------------------------------------------- |
| `chroma-styles.css` | Syntax highlighting theme (Catppuccin Macchiato)                        |
| `chroma-mod.css`    | Syntax highlighting layout adjustments                                  |
| `scroll-bar.css`    | Custom scrollbar styling (conditional, disabled by default)             |

### Extended

| File                | Purpose                                                                 |
| ------------------- | ----------------------------------------------------------------------- |
| `notice.css`        | Alert/notice boxes with 12 variants and dark mode support               |
| `typography.css`    | Public Sans font-face declarations                                      |

## Dark Mode Support

- **Implementation**: `data-theme="dark"` attribute on `<html>` element
- **Variables**: Separate color values defined for `[data-theme="dark"]` in:
  - `theme-vars.css` (lines 48-58)
  - `notice.css` (lines 116-193)
  - `head.html` noscript fallback (lines 112-141)
- **Theme Toggle**: Theme preference detection script in `head.html` (lines 156-192)
- **Storage**: Uses localStorage for `pref-theme` preference
- **Fallback**: Respects `prefers-color-scheme: dark` media query for system preferences

## Configuration

From `config.yml`:

- **Fingerprinting**: Enabled by default (adds hash to stylesheet filename for cache-busting)
- **Scroll Bar Style**: Disabled (`disableScrollBarStyle: true`)
- **Theme Variables**: Defined in `theme-vars.css`, not in config

## Build Output

- Production builds generate: `/public/assets/css/stylesheet.[hash].css`
- Hashes change when CSS content changes
- Integrity attribute included for subresource integrity (SRI) validation
- Preload directive (`rel="preload"`) for fast stylesheet loading
