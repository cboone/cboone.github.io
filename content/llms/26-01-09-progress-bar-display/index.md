---
date: 2026-01-16T13:13:32-05:00
sections: ["llms"]
title: "owloops/claude-powerline Progress Bar Display"
---

The [`owloops/claude-powerline`](https://github.com/Owloops/claude-powerline) status bar plugin for `code` [added a nice new setting today](https://github.com/Owloops/claude-powerline/blob/main/CHANGELOG.md#1150-2026-01-08). In your `~/.claude/claude-powerline.json` set the `.display.lines[0].segments.context.displayStyle` to `"bar"`, as so:

```json
{
  "display": {
    "lines": [
      {
        "segments": {
          "context": {
            "displayStyle":"bar",
            "enabled": true,
            "showPercentageOnly": true
          },
        }
      }
    ]
  },
}
```

This gives you a context segment that's simple and easy to read at a glance:

![Powerline status bar in Claude Code](status-bar.png)

Here's my full updated config that generates that style. (`theme` is set to `light` because that works best across light and dark terminal themes, I've found.)

```json
{
  "budget": {
    "session": {
      "amount": 67.5,
      "type": "tokens",
      "warningThreshold": 80
    }
  },
  "display": {
    "style": "capsule",
    "lines": [
      {
        "segments": {
          "directory": {
            "enabled": true,
            "style": "basename"
          },
          "git": {
            "enabled": true,
            "showSha": false,
            "showWorkingTree": true,
            "showOperation": true,
            "showTag": true,
            "showTimeSinceCommit": false,
            "showStashCount": true,
            "showUpstream": false,
            "showRepoName": false
          },
          "block": {
            "enabled": true,
            "type": "time",
            "burnType": "none"
          },
          "context": {
            "displayStyle":"bar",
            "enabled": true,
            "showPercentageOnly": true
          },
          "model": {
            "enabled": true
          }
        }
      }
    ]
  },
  "theme": "light"
}
```
