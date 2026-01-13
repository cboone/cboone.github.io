# Restore PaperMod Dark Mode Implementation

This document explains the differences between the pmichaillat/hugo-website fork and the original adityatelange/hugo-PaperMod theme regarding dark mode detection, and the changes required to restore the original functionality.

## The Bug

Dark mode auto-detection does not work on the homepage. The site fails to detect the system's `prefers-color-scheme: dark` preference on the homepage, while other pages work correctly.

## Root Cause Analysis

### PaperMod Original Implementation

The original PaperMod theme implements dark mode as follows:

1. **Detection script location:** `layouts/partials/head.html`
2. **CSS selector:** `:root[data-theme="dark"]`
3. **JavaScript approach:** Sets `data-theme` attribute on `<html>` element
4. **Toggle mechanism:** `html.dataset.theme = 'dark'`

This works because:
- The script is in `head.html`, which is included on ALL pages
- The `<html>` element exists when the script runs (even in `<head>`)
- Using a data attribute is clean and semantic

### pmichaillat Fork Implementation

The fork changed the implementation:

1. **Detection script location:** Moved to `layouts/partials/header.html`
2. **CSS selector:** Changed to `.dark` class
3. **JavaScript approach:** Adds `.dark` class to `<body>` element
4. **Toggle mechanism:** `document.body.classList.add('dark')`

This breaks because:
- In `layouts/_default/baseof.html`, there is a conditional:
  ```go
  {{- if not .IsHome }}
  {{- partialCached "header.html" . .Page -}}
  {{- end }}
  ```
- The `header.html` partial is NOT included on the homepage
- Therefore, the dark mode detection script never runs on the homepage

## Files Requiring Changes

### 1. `layouts/partials/head.html`

**Current (fork) approach:**
```javascript
if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
    document.documentElement.classList.add('dark');
}
```

**Required (PaperMod original) approach:**
```javascript
if (window.matchMedia('(prefers-color-scheme: dark)').matches) {
    document.querySelector("html").dataset.theme = 'dark';
} else {
    document.querySelector("html").dataset.theme = 'light';
}
```

The full script block handles three scenarios:
- User has saved preference in localStorage (priority)
- System prefers dark mode
- System prefers light mode (or no preference)

### 2. `layouts/partials/footer.html`

**Current (fork) approach:**
```javascript
document.getElementById("theme-toggle").addEventListener("click", () => {
    if (document.documentElement.className.includes("dark")) {
        document.body.classList.remove("dark");
        document.documentElement.classList.remove("dark");
        localStorage.setItem("pref-theme", "light");
    } else {
        document.body.classList.add("dark");
        document.documentElement.classList.add("dark");
        localStorage.setItem("pref-theme", "dark");
    }
});
```

**Required (PaperMod original) approach:**
```javascript
document.getElementById("theme-toggle").addEventListener("click", () => {
    const html = document.querySelector("html");
    if (html.dataset.theme === "dark") {
        html.dataset.theme = 'light';
        localStorage.setItem("pref-theme", 'light');
    } else {
        html.dataset.theme = 'dark';
        localStorage.setItem("pref-theme", 'dark');
    }
});
```

### 3. `assets/css/core/theme-vars.css`

**Current (fork) approach:**
```css
.dark {
    --theme: rgb(29, 30, 32);
    --entry: rgb(46, 46, 51);
    /* ... */
}

.dark.list {
    background: var(--theme);
}
```

**Required (PaperMod original) approach:**
```css
:root[data-theme="dark"] {
    --theme: rgb(29, 30, 32);
    --entry: rgb(46, 46, 51);
    /* ... */
}

[data-theme="dark"] .list {
    background: var(--theme);
}
```

### 4. `layouts/partials/header.html`

Remove the theme detection script entirely (lines 1-40 in the fork). The script should only exist in `head.html`.

## Why Restore PaperMod's Approach

1. **Correctness:** The script must be in `head.html` to run on all pages, including the homepage

2. **Timing:** Using `document.querySelector("html")` works in `<head>` because the `<html>` element exists. Using `document.body` would fail because `<body>` doesn't exist yet when `<head>` scripts run

3. **Maintainability:** Aligning with upstream PaperMod makes it easier to pull in updates and reduces divergence

4. **Semantics:** Using `data-theme` attribute is more semantic than CSS classes for theme state

## Implementation Checklist

- [ ] Update `head.html` detection script to use `dataset.theme`
- [ ] Update `footer.html` toggle to use `dataset.theme`
- [ ] Update `theme-vars.css` to use `:root[data-theme="dark"]` selector
- [ ] Remove duplicate script from `header.html` (if not already done)
- [ ] Test on homepage with system dark mode preference
- [ ] Test on other pages
- [ ] Test manual toggle functionality
- [ ] Test localStorage persistence across page loads

## References

- PaperMod original: https://github.com/adityatelange/hugo-PaperMod
- pmichaillat fork: https://github.com/pmichaillat/hugo-website
