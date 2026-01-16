---
title: "Verbose Mode"
date: 2026-01-10T10:53:25-05:00
---

{{< notice tip >}}

Turn on `code`'s verbose output mode. Unfortunately, it's a not something you can set in `~/.claude/settings.json`. But you can toggle it by running:

```bash
claude --verbose
```

Or by typing `control-o` during a session. Or by going into `/config` and toggling it on.

Once on, the setting will persist across `claude` instances and sessions.

{{< /notice >}}

As [the docs say](https://code.claude.com/docs/en/cli-reference) (also [here](https://code.claude.com/docs/en/common-workflows#configure-thinking-mode)), this serves to:

> Enable verbose logging, shows full turn-by-turn output (helpful for debugging in both print and interactive modes)

I find it very useful. Instead of seeing short summaries of what's going on, you see the entire output of what Claude's thinking through. Which makes it easier to catch when you're starting to descend into [a Claude Hole](https://www.reddit.com/r/sre/comments/1qbd255/new_term_claude_hole/). And also there are often interesting tidbits in the details that get left out of the final summaries.
