---
title: "Spacing Scale"
description: "Vertical rhythm and spacing scale based on a 6px unit"
---

<style>
.scale-grid {
    display: grid;
    gap: 0.5rem;
}

.scale-item {
    align-items: center;
    border: 1px solid var(--border-default);
    border-radius: var(--radius);
    display: grid;
    gap: 1rem;
    grid-template-columns: 140px 100px 1fr;
    overflow: hidden;
    padding: 0.75rem 1rem;
}

.scale-meta {
    display: flex;
    flex-direction: column;
    gap: 0.125rem;
}

.scale-var {
    font-family: "Iosevka Slab Extended", ui-monospace, monospace;
    font-size: 0.75rem;
    font-weight: var(--medium);
}

.scale-value {
    color: var(--text-muted);
    font-family: "Iosevka Slab Extended", ui-monospace, monospace;
    font-size: 0.75rem;
}

.scale-units {
    color: var(--text-muted);
    font-family: "Iosevka Slab Extended", ui-monospace, monospace;
    font-size: 0.75rem;
}

.scale-visual {
    align-items: center;
    display: flex;
}

.scale-bar {
    background: linear-gradient(135deg, #93a8d0 0%, #6a7ba2 100%);
    border-radius: 4px;
    height: 24px;
}

.spacing-demo {
    border: 1px solid var(--border-default);
    border-radius: var(--radius);
    margin-top: 1rem;
    padding: 1.5rem;
}

.spacing-demo-item {
    display: flex;
    flex-direction: column;
}

.spacing-demo-element {
    background: var(--background-code);
    border-radius: 4px;
    padding: 0.75rem 1rem;
}

.spacing-demo-element:first-child {
    font-family: "TASA Explorer", sans-serif;
    font-size: 1.25rem;
    font-weight: 800;
}

.spacing-demo-gap {
    align-items: center;
    background: linear-gradient(135deg, rgba(147, 168, 208, 0.3) 0%, rgba(106, 123, 162, 0.3) 100%);
    border-left: 3px solid #93a8d0;
    display: flex;
    justify-content: center;
}

.spacing-demo-label {
    background: var(--background-card);
    border-radius: 4px;
    color: #6a7ba2;
    font-family: "Iosevka Slab Extended", monospace;
    font-size: 0.7rem;
    padding: 0.125rem 0.5rem;
}

.comparison {
    display: grid;
    gap: 1.5rem;
    grid-template-columns: 1fr 1fr;
    margin-top: 1rem;
}

@media (max-width: 768px) {
    .comparison {
        grid-template-columns: 1fr;
    }
}

.comparison-block {
    border: 1px solid var(--border-default);
    border-radius: var(--radius);
    overflow: hidden;
}

.comparison-header {
    background: var(--background-code);
    border-bottom: 1px solid var(--border-default);
    padding: 0.75rem 1rem;
}

.comparison-header.bad {
    background: #fef2f2;
    border-color: #fecaca;
    color: #b91c1c;
}

.comparison-header.good {
    background: #f0fdf4;
    border-color: #bbf7d0;
    color: #15803d;
}

.comparison-content {
    padding: 1rem;
}

.comparison-content pre {
    background: var(--background-code);
    border-radius: 4px;
    font-family: "Iosevka Slab Extended", ui-monospace, monospace;
    font-size: 0.8rem;
    margin: 0;
    overflow-x: auto;
    padding: 0.75rem;
}

.intro-box {
    background: var(--background-code);
    border-left: 4px solid var(--accent-primary);
    border-radius: var(--radius);
    color: var(--text-muted);
    margin-bottom: 2rem;
    padding: 1.5rem;
}

.intro-box p:last-child {
    margin-bottom: 0;
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

.dark-preview .scale-item {
    border-color: #444;
}

.dark-preview .scale-value,
.dark-preview .scale-units {
    color: #aaa;
}
</style>

<div class="intro-box">
<p>This site uses a <strong>spacing scale</strong> based on a <strong>6px unit</strong> (one-third of the 18px base font size). All margins, padding, and gaps use multiples of this unit.</p>
<p>This is not a true baseline grid (which would require line-heights to be exact multiples of the unit). Instead, it provides <strong>consistent, proportional spacing</strong> between elements.</p>
</div>

## Spacing Scale

Base unit: 6px (1/3 of 18px body text)

<div class="scale-grid">
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--space-1</span>
            <span class="scale-value">6px</span>
        </div>
        <span class="scale-units">1 unit</span>
        <div class="scale-visual">
            <div class="scale-bar" style="width: 6px;"></div>
        </div>
    </div>
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--space-2</span>
            <span class="scale-value">12px</span>
        </div>
        <span class="scale-units">2 units</span>
        <div class="scale-visual">
            <div class="scale-bar" style="width: 12px;"></div>
        </div>
    </div>
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--space-3</span>
            <span class="scale-value">18px</span>
        </div>
        <span class="scale-units">3 units</span>
        <div class="scale-visual">
            <div class="scale-bar" style="width: 18px;"></div>
        </div>
    </div>
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--space-4</span>
            <span class="scale-value">24px</span>
        </div>
        <span class="scale-units">4 units</span>
        <div class="scale-visual">
            <div class="scale-bar" style="width: 24px;"></div>
        </div>
    </div>
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--space-5</span>
            <span class="scale-value">30px</span>
        </div>
        <span class="scale-units">5 units</span>
        <div class="scale-visual">
            <div class="scale-bar" style="width: 30px;"></div>
        </div>
    </div>
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--space-6</span>
            <span class="scale-value">36px</span>
        </div>
        <span class="scale-units">6 units</span>
        <div class="scale-visual">
            <div class="scale-bar" style="width: 36px;"></div>
        </div>
    </div>
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--space-8</span>
            <span class="scale-value">48px</span>
        </div>
        <span class="scale-units">8 units</span>
        <div class="scale-visual">
            <div class="scale-bar" style="width: 48px;"></div>
        </div>
    </div>
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--space-10</span>
            <span class="scale-value">60px</span>
        </div>
        <span class="scale-units">10 units</span>
        <div class="scale-visual">
            <div class="scale-bar" style="width: 60px;"></div>
        </div>
    </div>
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--space-12</span>
            <span class="scale-value">72px</span>
        </div>
        <span class="scale-units">12 units</span>
        <div class="scale-visual">
            <div class="scale-bar" style="width: 72px;"></div>
        </div>
    </div>
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--space-16</span>
            <span class="scale-value">96px</span>
        </div>
        <span class="scale-units">16 units</span>
        <div class="scale-visual">
            <div class="scale-bar" style="width: 96px;"></div>
        </div>
    </div>
</div>

---

## Usage Guidelines

### Recommended Use Cases

| Variable | Size | Use For |
|----------|------|---------|
| `--space-1` | 6px | Tight gaps, list item margins, small inline spacing |
| `--space-2` | 12px | Default gaps, button padding, card internal spacing |
| `--space-3` | 18px | Paragraph margins, image margins (matches base font) |
| `--space-4` | 24px | Section padding, content gaps, h5/h6 top margins |
| `--space-5` | 30px | Horizontal rules, h4 top margins |
| `--space-6` | 36px | h3 top margins, larger component spacing |
| `--space-8` | 48px | h1/h2 top margins, major section breaks |
| `--space-10` | 60px | Post footer margins, large section gaps |
| `--space-12` | 72px | Page-level spacing, hero sections |
| `--space-16` | 96px | Extra large gaps, footer/header heights |

### Layout Variables

The existing layout variables reference the spacing scale:

| Variable | Value | Use For |
|----------|-------|---------|
| `--gap` | var(--space-4) = 24px | Standard layout gap, container padding |
| `--content-gap` | var(--space-4) = 24px | Gap between content elements |

---

## Code Examples

<div class="comparison">
    <div class="comparison-block">
        <div class="comparison-header bad">Avoid: Magic Numbers</div>
        <div class="comparison-content">
            <pre>.component {
    margin-top: 47px;
    padding: 13px 22px;
    gap: 9px;
}</pre>
        </div>
    </div>
    <div class="comparison-block">
        <div class="comparison-header good">Use: Rhythm Variables</div>
        <div class="comparison-content">
            <pre>.component {
    margin-top: var(--space-8);
    padding: var(--space-2) var(--space-4);
    gap: var(--space-2);
}</pre>
        </div>
    </div>
</div>

### Heading Margins Pattern

Headings use larger top margins to create visual separation, with smaller bottom margins to connect with their content:

<div class="comparison">
    <div class="comparison-block">
        <div class="comparison-header good">Heading Spacing</div>
        <div class="comparison-content">
            <pre>.post-content h2 {
    /* More space above, less below */
    margin: var(--space-8) auto var(--space-4);
}

.post-content h3 {
    margin: var(--space-6) 0 var(--space-3);
}

.post-content h4 {
    margin: var(--space-5) 0 var(--space-2);
}</pre>
        </div>
    </div>
</div>

---

## Spacing in Practice

The colored bars show actual spacing values between elements:

<div class="spacing-demo">
    <div class="spacing-demo-item">
        <div class="spacing-demo-element">Heading</div>
        <div class="spacing-demo-gap" style="height: 24px;">
            <span class="spacing-demo-label">--space-4 (24px)</span>
        </div>
        <div class="spacing-demo-element">Paragraph text follows the heading with comfortable separation.</div>
        <div class="spacing-demo-gap" style="height: 24px;">
            <span class="spacing-demo-label">--space-4 (24px)</span>
        </div>
        <div class="spacing-demo-element">Another paragraph maintains the same rhythm.</div>
        <div class="spacing-demo-gap" style="height: 12px;">
            <span class="spacing-demo-label">--space-2 (12px)</span>
        </div>
        <div class="spacing-demo-element" style="font-size: var(--text-sm); color: var(--text-muted);">Tighter spacing groups related items like metadata.</div>
    </div>
</div>

---

## Design Rationale

### Why 6px?

The 6px base unit was chosen because:

- It divides evenly into the 18px base font size (18 / 3 = 6)
- It creates a flexible scale with useful intermediate values
- Common multiples (12, 24, 48) align with typical design expectations
- Small enough for fine control, large enough to be visually meaningful

### Why Not True Baseline Alignment?

True baseline grid alignment requires that line-height be an exact multiple of the rhythm unit. With 18px text and 1.5 line-height, each line is 27px tall, which doesn't divide evenly into 6px.

Achieving true baseline alignment would require either:

- Changing line-height to 24px (1.33) or 30px (1.67), which compromises readability
- Complex calculations for every element to compensate for the mismatch

The spacing scale approach provides 90% of the visual benefit with none of the complexity.

### Relationship to Typography

The spacing scale relates to the type scale:

| Typography | Size | Related Spacing |
|------------|------|-----------------|
| `--text-base` | 18px | `--space-3` (exact match) |
| `--text-sm` | 14px | `--space-2` (close: 12px) |
| `--text-lg` | 22px | `--space-4` (close: 24px) |

---

## Dark Mode

<div class="dark-preview">

### Spacing in Dark Mode

Vertical rhythm values remain consistent between light and dark modes. Only colors change, not spacing.

<div class="scale-grid" style="max-width: 400px;">
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--space-2</span>
            <span class="scale-value">12px</span>
        </div>
        <span class="scale-units">2 units</span>
        <div class="scale-visual">
            <div class="scale-bar" style="width: 12px; background: linear-gradient(135deg, #7aa2f7 0%, #93a8d0 100%);"></div>
        </div>
    </div>
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--space-4</span>
            <span class="scale-value">24px</span>
        </div>
        <span class="scale-units">4 units</span>
        <div class="scale-visual">
            <div class="scale-bar" style="width: 24px; background: linear-gradient(135deg, #7aa2f7 0%, #93a8d0 100%);"></div>
        </div>
    </div>
</div>

</div>
