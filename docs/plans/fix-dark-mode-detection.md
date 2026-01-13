# Fix Dark Mode Auto-Detection

## Problem

Dark mode does not automatically activate based on system preferences because:

1. **Script missing from `head.html`**: The theme detection script was removed from the customized `layouts/partials/head.html`
2. **Homepage exclusion**: The script in `header.html` is not loaded on the homepage due to `{{- if not .IsHome }}` condition in `baseof.html:20`
3. **CSS uses `.dark` selector**: The customized CSS expects a `.dark` class, which is compatible with the current `header.html` script approach

## Solution

Add the theme detection script to `layouts/partials/head.html` so it runs on all pages (including homepage) before content renders.

## Files to Modify

### 1. `layouts/partials/head.html`

Add the following block before the closing of the file (after line 154), matching the logic already in `header.html` but placed in `<head>` for earlier execution:

```html
{{- /* Theme detection script */}} {{- if (not site.Params.disableThemeToggle)
}} {{- if (eq site.Params.defaultTheme "light") }}
<script>
  if (localStorage.getItem("pref-theme") === "dark") {
    document.body.classList.add("dark");
  }
</script>
{{- else if (eq site.Params.defaultTheme "dark") }}
<script>
  if (localStorage.getItem("pref-theme") === "light") {
    document.body.classList.remove("dark");
  }
</script>
{{- else }} {{- /* theme is auto */}}
<script>
  if (localStorage.getItem("pref-theme") === "dark") {
    document.body.classList.add("dark");
  } else if (localStorage.getItem("pref-theme") === "light") {
    document.body.classList.remove("dark");
  } else if (window.matchMedia("(prefers-color-scheme: dark)").matches) {
    document.body.classList.add("dark");
  }
</script>
{{- end }} {{- else if (and (ne site.Params.defaultTheme "light") (ne
site.Params.defaultTheme "dark"))}}
<script>
  if (window.matchMedia("(prefers-color-scheme: dark)").matches) {
    document.body.classList.add("dark");
  }
</script>
{{- end }}
```

### 2. `layouts/partials/header.html`

Remove the duplicate theme detection script (lines 1-40) since it will now be in `head.html`. Keep only the `<header>` element and its contents (starting at line 42).

## No CSS Changes Required

The current CSS in `assets/css/core/theme-vars.css` uses `.dark` as the selector, which is compatible with the `document.body.classList.add('dark')` approach. No changes needed.

## Verification

1. Run `hugo server`
2. Open the site in Safari Technology Preview
3. Test on homepage (where the bug currently manifests)
4. Toggle system appearance in System Settings > Appearance
5. Verify dark mode activates/deactivates automatically
6. Test the manual toggle button works and persists preference
7. Verify other pages still work correctly
