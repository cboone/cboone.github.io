# GitHub Copilot Instructions

## PR Review Checklist (CRITICAL)

<!-- KEEP THIS SECTION UNDER 4000 CHARS - Copilot only reads first ~4000 -->

### Code Patterns - Do Not Flag

- **KaTeX retry mechanism**: The polling with maxRetries (100 retries at 50ms = 5s timeout) is intentional. This handles edge cases where deferred scripts load slowly. Do not suggest simplifying to DOMContentLoaded alone.
- **Imperative DOM manipulation in Alpine.js**: For dynamically generated content (like code blocks from markdown), imperative DOM manipulation in `x-init` is pragmatic and acceptable.
