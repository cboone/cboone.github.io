---
title: "Style Guide"
description: "A comprehensive reference of all styled elements used on this site"
---

This style guide documents all the styled elements available on this site. Use it to review typography, colors, components, and content elements.

## Typography

### Headings

Headings use **TASA Explorer** at weight 800. The type scale follows a Major Third ratio (1.25) with an 18px base.

# Heading 1 (44px)

## Heading 2 (35px)

### Heading 3 (28px)

#### Heading 4 (22px)

##### Heading 5 (18px, uppercase)

###### Heading 6 (14px, uppercase)

### Body Text

Body text uses **TASA Orbiter** at weight 400 with 18px size and 1.5 line height.

This is a paragraph of body text. The quick brown fox jumps over the lazy dog. Pack my box with five dozen liquor jugs. How vexingly quick daft zebras jump! This sentence demonstrates the readable line length and comfortable spacing between lines.

This is another paragraph showing the spacing between consecutive paragraphs. Good typography creates visual rhythm through consistent spacing.

### Text Styles

Regular text, **bold text**, *italic text*, ***bold italic text***, ~~strikethrough text~~, and `inline code`.

Here is a [link to demonstrate link styling](#typography), which has an underline accent.

---

## Lists

### Unordered List

- First item in the list
- Second item with more text to show how longer items wrap
- Third item
  - Nested item one
  - Nested item two
    - Deeply nested item
- Fourth item

### Ordered List

1. First numbered item
2. Second numbered item
3. Third numbered item
   1. Nested numbered item
   2. Another nested item
4. Fourth numbered item

### Definition List

Term One
: This is the definition for term one. It provides a description.

Term Two
: This is the definition for term two. Definition lists are useful for glossaries.

---

## Blockquotes

> This is a blockquote. It's styled with a left border and muted text color. Use blockquotes to highlight quoted content or important callouts.

> Blockquotes can span multiple paragraphs.
>
> This is the second paragraph in the blockquote.

---

## Code

### Inline Code

Use `const` to declare constants, `let` for block-scoped variables, and `var` for function-scoped variables.

Functions like `Array.prototype.map()` are essential for functional programming.

### Code Blocks

```javascript
// JavaScript example with syntax highlighting
function fibonacci(n) {
  if (n <= 1) return n;
  return fibonacci(n - 1) + fibonacci(n - 2);
}

const result = fibonacci(10);
console.log(`Fibonacci(10) = ${result}`);
```

```python
# Python example
def quick_sort(arr):
    if len(arr) <= 1:
        return arr
    pivot = arr[len(arr) // 2]
    left = [x for x in arr if x < pivot]
    middle = [x for x in arr if x == pivot]
    right = [x for x in arr if x > pivot]
    return quick_sort(left) + middle + quick_sort(right)
```

```css
/* CSS example */
.component {
  display: flex;
  align-items: center;
  gap: var(--space-4);
  background: var(--background-card);
  border-radius: var(--radius);
}
```

```bash
# Shell commands
hugo server --buildDrafts
git commit -m "Add new feature"
npm install && npm run build
```

---

## Tables

| Column 1 | Column 2 | Column 3 |
|----------|----------|----------|
| Row 1, Cell 1 | Row 1, Cell 2 | Row 1, Cell 3 |
| Row 2, Cell 1 | Row 2, Cell 2 | Row 2, Cell 3 |
| Row 3, Cell 1 | Row 3, Cell 2 | Row 3, Cell 3 |

### Table with Varied Content

| Feature | Description | Status |
|---------|-------------|--------|
| Dark Mode | Automatic theme switching | Active |
| Typography | TASA font family | Complete |
| Notices | 11 callout types | Complete |
| Timeline | Project showcase | Active |

---

## Notice Boxes

Notice boxes (callouts/admonitions) are available in 11 types. Each has distinct colors for light and dark modes.

{{< notice note >}}
This is a **note** notice. Use it for general notes and annotations.
{{< /notice >}}

{{< notice abstract >}}
This is an **abstract** notice. Use it for summaries and TL;DR sections. Aliases: `summary`, `tldr`.
{{< /notice >}}

{{< notice info >}}
This is an **info** notice. Use it for informational callouts.
{{< /notice >}}

{{< notice tip >}}
This is a **tip** notice. Use it for helpful tips and hints. Aliases: `hint`, `important`.
{{< /notice >}}

{{< notice success >}}
This is a **success** notice. Use it for success messages. Aliases: `check`, `done`.
{{< /notice >}}

{{< notice question >}}
This is a **question** notice. Use it for FAQs and questions. Aliases: `help`, `faq`.
{{< /notice >}}

{{< notice warning >}}
This is a **warning** notice. Use it for warnings and cautions. Aliases: `caution`, `attention`.
{{< /notice >}}

{{< notice danger >}}
This is a **danger** notice. Use it for dangerous or critical warnings. Aliases: `error`.
{{< /notice >}}

{{< notice failure >}}
This is a **failure** notice. Use it for failure states. Aliases: `fail`, `missing`.
{{< /notice >}}

{{< notice bug >}}
This is a **bug** notice. Use it for known bugs or issues.
{{< /notice >}}

{{< notice example >}}
This is an **example** notice. Use it for examples and demonstrations.
{{< /notice >}}

{{< notice todo >}}
This is a **todo** notice. Use it for todo items and pending tasks.
{{< /notice >}}

{{< notice quote >}}
This is a **quote** notice. Use it for quotations with attribution. Alias: `cite`.
{{< /notice >}}

### Notice with Custom Title

{{< notice type="tip" title="Pro Tip" >}}
You can customize the notice title using the `title` parameter.
{{< /notice >}}

### Notice with Complex Content

{{< notice type="example" title="Code Example" >}}
Notices can contain code blocks and other markdown:

```go
package main

import "fmt"

func main() {
    fmt.Println("Hello from a notice!")
}
```

They can also include lists:
- Item one
- Item two
- Item three
{{< /notice >}}

---

## Images

Images have rounded corners and appropriate margins.

![Sample image placeholder](https://via.placeholder.com/720x400/f6f8fa/6a7ba2?text=Sample+Image)

### Centered Image

Images can be centered using the `#center` fragment:

![Centered image](https://via.placeholder.com/400x200/eef1f5/93a8d0?text=Centered#center)

---

## Horizontal Rules

Horizontal rules provide visual separation between sections. See the lines between major sections on this page.

---

## Mixed Content Example

Here's an example combining multiple elements:

### Building a Feature

When implementing a new feature, follow these steps:

1. **Plan the implementation**
   - Review requirements
   - Identify affected components

2. **Write the code**

   ```javascript
   function newFeature() {
     // Implementation here
     return result;
   }
   ```

3. **Test thoroughly**

{{< notice warning >}}
Always run the full test suite before committing changes.
{{< /notice >}}

> "Code is read more often than it is written." — Guido van Rossum

| Phase | Duration | Owner |
|-------|----------|-------|
| Planning | 2 days | Team Lead |
| Development | 5 days | Developer |
| Testing | 2 days | QA |

---

## Related References

For more detailed documentation of design tokens:

- **Colors**: See `/styles/colors/` for the complete color palette
- **Typography**: See `/styles/typography/` for font families and scales
- **Spacing**: See `/styles/rhythm/` for the spacing scale

---

## Dark Mode

Toggle the theme using the sun/moon icon in the header to see how all elements adapt to dark mode. All components are designed to work well in both light and dark themes.
