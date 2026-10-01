---
title: "Colors"
description: "Color palette and CSS custom properties for light and dark modes"
---

<style>
.color-grid {
    display: grid;
    gap: 1rem;
    grid-template-columns: repeat(auto-fill, minmax(200px, 1fr));
    margin-bottom: 1.5rem;
}

.swatch {
    border: 1px solid var(--border-default);
    border-radius: var(--radius);
    overflow: hidden;
}

.swatch-color {
    height: 80px;
}

.swatch-info {
    background: var(--background-card);
    font-size: var(--text-sm);
    padding: 0.75rem;
}

.swatch-name {
    font-weight: var(--medium);
    margin-bottom: 0.25rem;
}

.swatch-value {
    color: var(--text-muted);
    font-family: "Iosevka Slab Extended", ui-monospace, monospace;
    font-size: 0.75rem;
}

.notice-swatch {
    border: 1px solid var(--border-default);
    border-radius: var(--radius);
    overflow: hidden;
}

.notice-swatch-color {
    align-items: center;
    border-left: 6px solid;
    display: flex;
    font-family: "Iosevka Slab Extended", ui-monospace, monospace;
    font-size: var(--text-sm);
    font-weight: var(--medium);
    height: 60px;
    padding-left: 1rem;
}

.notice-swatch-info {
    background: var(--background-card);
    display: grid;
    font-size: 0.7rem;
    gap: 0.125rem;
    grid-template-columns: repeat(3, 1fr);
    padding: 0.5rem;
}

.notice-swatch-info span {
    font-family: "Iosevka Slab Extended", ui-monospace, monospace;
    color: var(--text-muted);
}

.dark-preview {
    background: rgb(29, 30, 32);
    border-radius: var(--radius);
    color: rgb(196, 196, 197);
    margin-top: 1rem;
    padding: 1.5rem;
}

.dark-preview h3 {
    color: #fff;
    margin-top: 0;
}

.dark-preview .swatch {
    border-color: #444;
}

.dark-preview .swatch-info {
    background: rgb(46, 46, 51);
    color: #fff;
}

.dark-preview .swatch-value {
    color: #aaa;
}

.dark-preview .notice-swatch {
    border-color: #444;
}

.dark-preview .notice-swatch-info {
    background: rgb(46, 46, 51);
}

.dark-preview .notice-swatch-info span {
    color: #aaa;
}
</style>

This page documents all CSS custom properties for colors used throughout the site, including light and dark mode variants.

## Backgrounds

### Light Mode

<div class="color-grid">
    <div class="swatch">
        <div class="swatch-color" style="background: #f6f8fa;"></div>
        <div class="swatch-info">
            <div class="swatch-name">--background-page</div>
            <div class="swatch-value">#f6f8fa</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(255, 255, 255);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--background-card</div>
            <div class="swatch-value">rgb(255, 255, 255)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: #eef1f5;"></div>
        <div class="swatch-info">
            <div class="swatch-name">--background-code</div>
            <div class="swatch-value">#eef1f5</div>
        </div>
    </div>
</div>

<div class="dark-preview">

### Dark Mode

<div class="color-grid">
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(29, 30, 32);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--background-page</div>
            <div class="swatch-value">rgb(29, 30, 32)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(46, 46, 51);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--background-card</div>
            <div class="swatch-value">rgb(46, 46, 51)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(36, 39, 46);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--background-code</div>
            <div class="swatch-value">rgb(36, 39, 46)</div>
        </div>
    </div>
</div>

</div>

### Usage

| Variable | Use For |
|----------|---------|
| `--background-page` | All page backgrounds (body element), base background color |
| `--background-card` | Cards, elevated surfaces, post entries (creates contrast on list pages) |
| `--background-code` | Code blocks, inline code, list page backgrounds (light mode) |
| `--background-page-rgb` | When you need `--background-page` with opacity (e.g., `rgba(var(--background-page-rgb), 0.85)`) |

---

## Text

### Light Mode

<div class="color-grid">
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(30, 30, 30);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--text-heading</div>
            <div class="swatch-value">rgb(30, 30, 30)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(30, 30, 30);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--text-body</div>
            <div class="swatch-value">rgb(30, 30, 30)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(108, 108, 108);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--text-muted</div>
            <div class="swatch-value">rgb(108, 108, 108)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(165, 165, 165);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--text-subtle</div>
            <div class="swatch-value">rgb(165, 165, 165)</div>
        </div>
    </div>
</div>

<div class="dark-preview">

### Dark Mode

<div class="color-grid">
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(218, 218, 219);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--text-heading</div>
            <div class="swatch-value">rgb(218, 218, 219)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(196, 196, 197);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--text-body</div>
            <div class="swatch-value">rgb(196, 196, 197)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(155, 156, 157);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--text-muted</div>
            <div class="swatch-value">rgb(155, 156, 157)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(165, 165, 165);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--text-subtle</div>
            <div class="swatch-value">rgb(165, 165, 165)</div>
        </div>
    </div>
</div>

</div>

### Usage

| Variable | Use For |
|----------|---------|
| `--text-heading` | Headings, buttons, high-emphasis text |
| `--text-body` | Body text, main content |
| `--text-muted` | Metadata, descriptions, muted text, footer |
| `--text-subtle` | h4/h5 headings, very muted text |

---

## Accents and Borders

### Light Mode

<div class="color-grid">
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(238, 238, 238);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--border-default</div>
            <div class="swatch-value">rgb(238, 238, 238)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(214, 214, 214);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--border-subtle</div>
            <div class="swatch-value">rgb(214, 214, 214)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: #93a8d0;"></div>
        <div class="swatch-info">
            <div class="swatch-name">--accent-primary</div>
            <div class="swatch-value">#93a8d0</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: #6a7ba2;"></div>
        <div class="swatch-info">
            <div class="swatch-name">--accent-secondary</div>
            <div class="swatch-value">#6a7ba2</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: #cbd1de;"></div>
        <div class="swatch-info">
            <div class="swatch-name">--accent-tertiary</div>
            <div class="swatch-value">#cbd1de</div>
        </div>
    </div>
</div>

<div class="dark-preview">

### Dark Mode

<div class="color-grid">
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(51, 51, 51);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--border-default</div>
            <div class="swatch-value">rgb(51, 51, 51)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(65, 66, 68);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--border-subtle</div>
            <div class="swatch-value">rgb(65, 66, 68)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: #7aa2f7;"></div>
        <div class="swatch-info">
            <div class="swatch-name">--accent-primary</div>
            <div class="swatch-value">#7aa2f7</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: #93a8d0;"></div>
        <div class="swatch-info">
            <div class="swatch-name">--accent-secondary</div>
            <div class="swatch-value">#93a8d0</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: #6a7ba2;"></div>
        <div class="swatch-info">
            <div class="swatch-name">--accent-tertiary</div>
            <div class="swatch-value">#6a7ba2</div>
        </div>
    </div>
</div>

</div>

### Usage

| Variable | Use For |
|----------|---------|
| `--accent-primary` | Links, interactive elements, hover underlines, active states |
| `--accent-secondary` | Secondary accent color, dark mode social icon hover |
| `--accent-tertiary` | Hover backgrounds, button backgrounds, subtle accents |
| `--border-default` | Element borders, dividers |
| `--border-subtle` | Borders, list markers, subtle accents, scroll-to-top button |

---

## Scrollbar Colors

### Light Mode

<div class="color-grid">
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(113, 113, 117);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--scrollbar-code-thumb</div>
            <div class="swatch-value">rgb(113, 113, 117)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(163, 163, 165);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--scrollbar-code-thumb-hover</div>
            <div class="swatch-value">rgb(163, 163, 165)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(173, 173, 173);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--scrollbar-gist-thumb</div>
            <div class="swatch-value">rgb(173, 173, 173)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(112, 112, 112);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--scrollbar-gist-thumb-hover</div>
            <div class="swatch-value">rgb(112, 112, 112)</div>
        </div>
    </div>
</div>

<div class="dark-preview">

### Dark Mode

<div class="color-grid">
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(155, 156, 157);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--scrollbar-code-thumb</div>
            <div class="swatch-value">rgb(155, 156, 157)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(180, 180, 182);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--scrollbar-code-thumb-hover</div>
            <div class="swatch-value">rgb(180, 180, 182)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(100, 100, 105);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--scrollbar-gist-thumb</div>
            <div class="swatch-value">rgb(100, 100, 105)</div>
        </div>
    </div>
    <div class="swatch">
        <div class="swatch-color" style="background: rgb(140, 140, 145);"></div>
        <div class="swatch-info">
            <div class="swatch-name">--scrollbar-gist-thumb-hover</div>
            <div class="swatch-value">rgb(140, 140, 145)</div>
        </div>
    </div>
</div>

</div>

### Usage

| Variable | Use For |
|----------|---------|
| `--scrollbar-code-thumb` | Code block scrollbar thumb |
| `--scrollbar-code-thumb-hover` | Code block scrollbar thumb on hover |
| `--scrollbar-gist-thumb` | GitHub Gist embed scrollbar thumb |
| `--scrollbar-gist-thumb-hover` | GitHub Gist embed scrollbar thumb on hover |

---

## Notice Colors

Each notice type has three variables: `--notice-{type}-bg`, `--notice-{type}-border`, `--notice-{type}-text`

### Light Mode

<div class="color-grid">
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: #ecfdf5; border-color: #10b981; color: #047857;">abstract</div>
        <div class="notice-swatch-info">
            <span>#ecfdf5</span>
            <span>#10b981</span>
            <span>#047857</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: #fef2f2; border-color: #dc2626; color: #b91c1c;">danger</div>
        <div class="notice-swatch-info">
            <span>#fef2f2</span>
            <span>#dc2626</span>
            <span>#b91c1c</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: #faf5ff; border-color: #a855f7; color: #7e22ce;">example</div>
        <div class="notice-swatch-info">
            <span>#faf5ff</span>
            <span>#a855f7</span>
            <span>#7e22ce</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: #eff6ff; border-color: #3b82f6; color: #1d4ed8;">info</div>
        <div class="notice-swatch-info">
            <span>#eff6ff</span>
            <span>#3b82f6</span>
            <span>#1d4ed8</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: #eff6ff; border-color: #6366f1; color: #4338ca;">note</div>
        <div class="notice-swatch-info">
            <span>#eff6ff</span>
            <span>#6366f1</span>
            <span>#4338ca</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: #fffbeb; border-color: #f59e0b; color: #b45309;">question</div>
        <div class="notice-swatch-info">
            <span>#fffbeb</span>
            <span>#f59e0b</span>
            <span>#b45309</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: #f9fafb; border-color: #9ca3af; color: #4b5563;">quote</div>
        <div class="notice-swatch-info">
            <span>#f9fafb</span>
            <span>#9ca3af</span>
            <span>#4b5563</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: #f0fdf4; border-color: #22c55e; color: #15803d;">success</div>
        <div class="notice-swatch-info">
            <span>#f0fdf4</span>
            <span>#22c55e</span>
            <span>#15803d</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: #f0fdfa; border-color: #14b8a6; color: #0f766e;">tip</div>
        <div class="notice-swatch-info">
            <span>#f0fdfa</span>
            <span>#14b8a6</span>
            <span>#0f766e</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: #fdf4ff; border-color: #c026d3; color: #a21caf;">todo</div>
        <div class="notice-swatch-info">
            <span>#fdf4ff</span>
            <span>#c026d3</span>
            <span>#a21caf</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: #fff7ed; border-color: #f97316; color: #c2410c;">warning</div>
        <div class="notice-swatch-info">
            <span>#fff7ed</span>
            <span>#f97316</span>
            <span>#c2410c</span>
        </div>
    </div>
</div>

<div class="dark-preview">

### Dark Mode

<div class="color-grid">
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: rgba(16, 185, 129, 0.1); border-color: #34d399; color: #6ee7b7;">abstract</div>
        <div class="notice-swatch-info">
            <span>rgba(16,185,129,0.1)</span>
            <span>#34d399</span>
            <span>#6ee7b7</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: rgba(220, 38, 38, 0.1); border-color: #f87171; color: #fca5a5;">danger</div>
        <div class="notice-swatch-info">
            <span>rgba(220,38,38,0.1)</span>
            <span>#f87171</span>
            <span>#fca5a5</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: rgba(168, 85, 247, 0.1); border-color: #c084fc; color: #d8b4fe;">example</div>
        <div class="notice-swatch-info">
            <span>rgba(168,85,247,0.1)</span>
            <span>#c084fc</span>
            <span>#d8b4fe</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: rgba(59, 130, 246, 0.1); border-color: #60a5fa; color: #93c5fd;">info</div>
        <div class="notice-swatch-info">
            <span>rgba(59,130,246,0.1)</span>
            <span>#60a5fa</span>
            <span>#93c5fd</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: rgba(99, 102, 241, 0.1); border-color: #818cf8; color: #a5b4fc;">note</div>
        <div class="notice-swatch-info">
            <span>rgba(99,102,241,0.1)</span>
            <span>#818cf8</span>
            <span>#a5b4fc</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: rgba(245, 158, 11, 0.1); border-color: #fbbf24; color: #fcd34d;">question</div>
        <div class="notice-swatch-info">
            <span>rgba(245,158,11,0.1)</span>
            <span>#fbbf24</span>
            <span>#fcd34d</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: rgba(156, 163, 175, 0.1); border-color: #9ca3af; color: #d1d5db;">quote</div>
        <div class="notice-swatch-info">
            <span>rgba(156,163,175,0.1)</span>
            <span>#9ca3af</span>
            <span>#d1d5db</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: rgba(34, 197, 94, 0.1); border-color: #4ade80; color: #86efac;">success</div>
        <div class="notice-swatch-info">
            <span>rgba(34,197,94,0.1)</span>
            <span>#4ade80</span>
            <span>#86efac</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: rgba(20, 184, 166, 0.1); border-color: #2dd4bf; color: #5eead4;">tip</div>
        <div class="notice-swatch-info">
            <span>rgba(20,184,166,0.1)</span>
            <span>#2dd4bf</span>
            <span>#5eead4</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: rgba(192, 38, 211, 0.1); border-color: #e879f9; color: #f0abfc;">todo</div>
        <div class="notice-swatch-info">
            <span>rgba(192,38,211,0.1)</span>
            <span>#e879f9</span>
            <span>#f0abfc</span>
        </div>
    </div>
    <div class="notice-swatch">
        <div class="notice-swatch-color" style="background: rgba(249, 115, 22, 0.1); border-color: #fb923c; color: #fdba74;">warning</div>
        <div class="notice-swatch-info">
            <span>rgba(249,115,22,0.1)</span>
            <span>#fb923c</span>
            <span>#fdba74</span>
        </div>
    </div>
</div>

</div>

### Notice Type Reference

| Type | Variables | Use For |
|------|-----------|---------|
| `abstract` | `--notice-abstract-*` | Summaries, abstracts (green) |
| `danger` | `--notice-danger-*` | Danger, bug, failure warnings (red) |
| `example` | `--notice-example-*` | Examples (purple) |
| `info` | `--notice-info-*` | Information callouts (blue) |
| `note` | `--notice-note-*` | Notes (indigo) |
| `question` | `--notice-question-*` | Questions (amber) |
| `quote` | `--notice-quote-*` | Quotations (gray) |
| `success` | `--notice-success-*` | Success messages (green) |
| `tip` | `--notice-tip-*` | Tips (teal) |
| `todo` | `--notice-todo-*` | Todo items (fuchsia) |
| `warning` | `--notice-warning-*` | Warnings (orange) |
