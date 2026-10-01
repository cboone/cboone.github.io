---
title: "Typography"
description: "Font families, type scale, weights, line heights, and letter spacing"
---

<style>
.font-demo {
    border: 1px solid var(--border-default);
    border-radius: var(--radius);
    margin-bottom: 1rem;
    overflow: hidden;
}

.font-demo-header {
    background: var(--background-code);
    border-bottom: 1px solid var(--border-default);
    padding: 0.75rem 1rem;
}

.font-demo-name {
    font-weight: var(--medium);
    margin-bottom: 0.25rem;
}

.font-demo-meta {
    color: var(--text-muted);
    font-family: "Iosevka Slab Extended", ui-monospace, monospace;
    font-size: 0.75rem;
}

.font-demo-sample {
    padding: 1.5rem 1rem;
}

.alphabet-sample {
    color: var(--text-muted);
    font-size: var(--text-sm);
    margin-top: 0.5rem;
}

.scale-grid {
    display: grid;
    gap: 1rem;
}

.scale-item {
    align-items: baseline;
    border: 1px solid var(--border-default);
    border-radius: var(--radius);
    display: grid;
    gap: 1rem;
    grid-template-columns: 120px 1fr;
    overflow: hidden;
    padding: 1rem;
}

.scale-meta {
    display: flex;
    flex-direction: column;
    gap: 0.25rem;
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

.weight-samples {
    display: grid;
    gap: 0.5rem;
}

.weight-sample {
    align-items: center;
    border: 1px solid var(--border-default);
    border-radius: var(--radius);
    display: grid;
    gap: 1rem;
    grid-template-columns: 140px 1fr;
    padding: 0.75rem 1rem;
}

.weight-meta {
    display: flex;
    flex-direction: column;
    gap: 0.125rem;
}

.weight-var {
    font-family: "Iosevka Slab Extended", ui-monospace, monospace;
    font-size: 0.75rem;
    font-weight: var(--medium);
}

.weight-value {
    color: var(--text-muted);
    font-family: "Iosevka Slab Extended", ui-monospace, monospace;
    font-size: 0.75rem;
}

.spacing-samples {
    display: grid;
    gap: 0.5rem;
}

.spacing-sample {
    border: 1px solid var(--border-default);
    border-radius: var(--radius);
    overflow: hidden;
}

.spacing-header {
    background: var(--background-code);
    border-bottom: 1px solid var(--border-default);
    display: flex;
    gap: 1rem;
    padding: 0.5rem 1rem;
}

.spacing-var {
    font-family: "Iosevka Slab Extended", ui-monospace, monospace;
    font-size: 0.75rem;
    font-weight: var(--medium);
}

.spacing-value {
    color: var(--text-muted);
    font-family: "Iosevka Slab Extended", ui-monospace, monospace;
    font-size: 0.75rem;
}

.spacing-preview {
    font-family: "TASA Explorer", -apple-system, sans-serif;
    font-size: 1.25rem;
    font-weight: 800;
    padding: 1rem;
}

.leading-preview {
    background: linear-gradient(to bottom, transparent 49%, rgba(147, 168, 208, 0.3) 49%, rgba(147, 168, 208, 0.3) 51%, transparent 51%);
    font-size: 1rem;
    padding: 1rem;
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

.dark-preview .font-demo {
    border-color: #444;
}

.dark-preview .font-demo-header {
    background: rgb(46, 46, 51);
    border-color: #444;
    color: #fff;
}

.dark-preview .font-demo-meta {
    color: #aaa;
}
</style>

This page documents the typography system including font families, type scale, weights, and spacing.

## Font Families

<div class="font-demo">
    <div class="font-demo-header">
        <div class="font-demo-name">TASA Explorer</div>
        <div class="font-demo-meta">Headings, navigation, footer | Weight: 800</div>
    </div>
    <div class="font-demo-sample">
        <div style="font-family: 'TASA Explorer', sans-serif; font-size: 2rem; font-weight: 800; margin-bottom: 0.5rem;">The quick brown fox jumps over the lazy dog</div>
        <div class="alphabet-sample" style="font-family: 'TASA Explorer', sans-serif; font-weight: 800;">
            ABCDEFGHIJKLMNOPQRSTUVWXYZ<br>
            abcdefghijklmnopqrstuvwxyz<br>
            0123456789
        </div>
    </div>
</div>

<div class="font-demo">
    <div class="font-demo-header">
        <div class="font-demo-name">TASA Orbiter</div>
        <div class="font-demo-meta">Body text | Weight: 400</div>
    </div>
    <div class="font-demo-sample">
        <div style="font-size: 18px; line-height: 1.5; margin-bottom: 0.5rem;">The quick brown fox jumps over the lazy dog. Pack my box with five dozen liquor jugs. How vexingly quick daft zebras jump!</div>
        <div class="alphabet-sample">
            ABCDEFGHIJKLMNOPQRSTUVWXYZ<br>
            abcdefghijklmnopqrstuvwxyz<br>
            0123456789
        </div>
    </div>
</div>

<div class="font-demo">
    <div class="font-demo-header">
        <div class="font-demo-name">Iosevka Slab Extended</div>
        <div class="font-demo-meta">Code, inline code, preformatted text | Weight: 400</div>
    </div>
    <div class="font-demo-sample">
        <div style="font-family: 'Iosevka Slab Extended', ui-monospace, monospace; font-size: 16px; line-height: 1.5; margin-bottom: 0.5rem;">const greeting = "Hello, World!";<br>function fibonacci(n) { return n <= 1 ? n : fibonacci(n - 1) + fibonacci(n - 2); }</div>
        <div class="alphabet-sample" style="font-family: 'Iosevka Slab Extended', monospace;">
            ABCDEFGHIJKLMNOPQRSTUVWXYZ<br>
            abcdefghijklmnopqrstuvwxyz<br>
            0123456789 !@#$%^&*()_+-=[]{}|;':",<>.?/
        </div>
    </div>
</div>

### Usage

| Font | CSS Declaration | Use For |
|------|-----------------|---------|
| TASA Explorer | `font-family: "TASA Explorer", -apple-system, ...` | h1-h6, .logo, #menu, .footer |
| TASA Orbiter | `font-family: "TASA Orbiter", -apple-system, ...` | body, all content text |
| Iosevka Slab Extended | `font-family: "Iosevka Slab Extended", ui-monospace, ...` | code, kbd, pre, samp |

---

## Type Scale

Major Third ratio (1.25), base 18px

<div class="scale-grid">
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--text-3xl</span>
            <span class="scale-value">44px</span>
        </div>
        <div style="font-size: 44px; line-height: 1.25;">Display</div>
    </div>
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--text-2xl</span>
            <span class="scale-value">35px</span>
        </div>
        <div style="font-size: 35px; line-height: 1.25;">Heading 1</div>
    </div>
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--text-xl</span>
            <span class="scale-value">28px</span>
        </div>
        <div style="font-size: 28px; line-height: 1.25;">Heading 2</div>
    </div>
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--text-lg</span>
            <span class="scale-value">22px</span>
        </div>
        <div style="font-size: 22px; line-height: 1.25;">Heading 3</div>
    </div>
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--text-base</span>
            <span class="scale-value">18px</span>
        </div>
        <div style="font-size: 18px;">Body text (base size)</div>
    </div>
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--text-sm</span>
            <span class="scale-value">14px</span>
        </div>
        <div style="font-size: 14px;">Small text, metadata</div>
    </div>
    <div class="scale-item">
        <div class="scale-meta">
            <span class="scale-var">--text-xs</span>
            <span class="scale-value">11px</span>
        </div>
        <div style="font-size: 11px;">Extra small, captions</div>
    </div>
</div>

### Usage

| Variable | Size | Use For |
|----------|------|---------|
| `--text-3xl` | 44px | Hero titles, display text |
| `--text-2xl` | 35px | Page titles, h1 elements |
| `--text-xl` | 28px | Section headers, h2 elements |
| `--text-lg` | 22px | Subsection headers, h3 elements |
| `--text-base` | 18px | Body text, paragraphs, default size |
| `--text-sm` | 14px | Metadata, timestamps, secondary info |
| `--text-xs` | 11px | Captions, fine print |

---

## Font Weights

<div class="weight-samples">
    <div class="weight-sample">
        <div class="weight-meta">
            <span class="weight-var">--normal</span>
            <span class="weight-value">400</span>
        </div>
        <div style="font-weight: 400;">Regular body text weight</div>
    </div>
    <div class="weight-sample">
        <div class="weight-meta">
            <span class="weight-var">--medium</span>
            <span class="weight-value">500</span>
        </div>
        <div style="font-weight: 500;">Medium emphasis text</div>
    </div>
    <div class="weight-sample">
        <div class="weight-meta">
            <span class="weight-var">--semibold</span>
            <span class="weight-value">500</span>
        </div>
        <div style="font-weight: 500;">Semibold (same as medium)</div>
    </div>
    <div class="weight-sample">
        <div class="weight-meta">
            <span class="weight-var">--bold</span>
            <span class="weight-value">700</span>
        </div>
        <div style="font-weight: 700;">Bold emphasis text</div>
    </div>
</div>

### Usage

| Variable | Weight | Use For |
|----------|--------|---------|
| `--normal` | 400 | Body text, regular content |
| `--medium` | 500 | Slightly emphasized text |
| `--semibold` | 500 | Alias for medium weight |
| `--bold` | 700 | Strong emphasis, important text |

Note: TASA Explorer headings use weight 800 (extra bold) directly, not these variables.

---

## Line Height

<div class="spacing-samples">
    <div class="spacing-sample">
        <div class="spacing-header">
            <span class="spacing-var">--leading-tight</span>
            <span class="spacing-value">1.25</span>
        </div>
        <div class="leading-preview" style="line-height: 1.25;">
            Tight line height for headings and display text where vertical rhythm needs to be compact. This creates a more condensed feel that works well with larger type sizes.
        </div>
    </div>
    <div class="spacing-sample">
        <div class="spacing-header">
            <span class="spacing-var">--leading-normal</span>
            <span class="spacing-value">1.5</span>
        </div>
        <div class="leading-preview" style="line-height: 1.5;">
            Normal line height for body text and paragraphs. This provides comfortable reading with adequate space between lines, improving readability for longer content blocks.
        </div>
    </div>
</div>

### Usage

| Variable | Value | Use For |
|----------|-------|---------|
| `--leading-tight` | 1.25 | Headings, display text, compact layouts |
| `--leading-normal` | 1.5 | Body text, paragraphs, readable content |

---

## Letter Spacing

<div class="spacing-samples">
    <div class="spacing-sample">
        <div class="spacing-header">
            <span class="spacing-var">--tracking-tighter</span>
            <span class="spacing-value">-0.02em</span>
        </div>
        <div class="spacing-preview" style="letter-spacing: -0.02em;">
            TIGHTER TRACKING FOR LARGE HEADINGS
        </div>
    </div>
    <div class="spacing-sample">
        <div class="spacing-header">
            <span class="spacing-var">(default)</span>
            <span class="spacing-value">0</span>
        </div>
        <div class="spacing-preview">
            DEFAULT LETTER SPACING
        </div>
    </div>
    <div class="spacing-sample">
        <div class="spacing-header">
            <span class="spacing-var">--tracking-wide</span>
            <span class="spacing-value">0.025em</span>
        </div>
        <div class="spacing-preview" style="letter-spacing: 0.025em;">
            WIDE TRACKING FOR SMALL CAPS
        </div>
    </div>
</div>

### Usage

| Variable | Value | Use For |
|----------|-------|---------|
| `--tracking-tighter` | -0.02em | Large display headings where default spacing looks too loose |
| `--tracking-wide` | 0.025em | Small caps, uppercase labels, buttons |

---

## Dark Mode Preview

<div class="dark-preview">

### Typography in Dark Mode

Typography settings remain consistent between light and dark modes. Only text colors change:

<div class="font-demo">
    <div class="font-demo-header">
        <div class="font-demo-name" style="color: rgb(218, 218, 219);">Heading Text</div>
        <div class="font-demo-meta">--text-heading: rgb(218, 218, 219)</div>
    </div>
    <div class="font-demo-sample">
        <div style="font-family: 'TASA Explorer', sans-serif; font-size: 2rem; font-weight: 800; color: rgb(218, 218, 219);">The quick brown fox</div>
    </div>
</div>

<div class="font-demo" style="margin-top: 1rem;">
    <div class="font-demo-header">
        <div class="font-demo-name" style="color: rgb(196, 196, 197);">Body Text</div>
        <div class="font-demo-meta">--text-body: rgb(196, 196, 197)</div>
    </div>
    <div class="font-demo-sample">
        <div style="color: rgb(196, 196, 197);">Pack my box with five dozen liquor jugs. How vexingly quick daft zebras jump!</div>
    </div>
</div>

<div class="font-demo" style="margin-top: 1rem;">
    <div class="font-demo-header">
        <div class="font-demo-name" style="color: rgb(155, 156, 157);">Muted Text</div>
        <div class="font-demo-meta">--text-muted: rgb(155, 156, 157)</div>
    </div>
    <div class="font-demo-sample">
        <div style="color: rgb(155, 156, 157);">Metadata, descriptions, and secondary information use muted colors.</div>
    </div>
</div>

</div>
