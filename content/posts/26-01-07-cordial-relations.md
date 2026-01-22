---
date: 2026-01-07T10:30:00-05:00
sections: ["llms"]
title: "Notes on cordial relationships with our new overlords"
ShowToc: true
---

Written for a friend who's getting started with the LLMs, Claude Code specifically.

In no particular order.

## Superstition

Everyone's got their own superstitions / rituals / incantations / whatever related to using the magic robots. I'm no exception.

My approach is to talk to Claude the way I want Claude to talk to me. Intelligently, articulately, precisely, clearly. I use full sentences and proper grammar. Even periods most of the time! I don't swear, I don't complain, I don't make jokes, I just tell it what I want. And I never get any weird behavior back, none of the crazy stuff that so many other people seem to run into.

A lot of the time I express myself as if I were writing a technical story for a client PM to read. Someone smart and experienced, who will appreciate clarity and precision.

The LLM architecture is such that they're designed to reflect back to us what we give them. Seems straightforward to me to communicate with it with as much sophistication as I can.

YMMV.

## Usage

Don't use `/usage` in the console, it counts against you. Seems like a bug.

I use [`owloops/claude-powerline`](https://github.com/Owloops/claude-powerline) to show me the usage in an ongoing way. I believe it uses data that comes back from the API with every request, so no extra calls being made. It takes a little futzing to get it set up correctly. I'll paste my config down below.

There's also [`hamed-elfayome/Claude-Usage-Tracker`](https://github.com/hamed-elfayome/Claude-Usage-Tracker), which is a macOS menu bar widget. Looks cool, I haven't gotten around to setting it up yet.

## General workflow

At a minimum I typically have one terminal open with `claude` running and one for `git`. Maybe one for tests and / or one for manual testing as well. Then I've got my repo open in VSCodium, which has GitHub Copilot going, both for autocomplete and chat. The chat I have connected to my Anthropic account, so that uses tokens via the api. VSCodium's not actually my favorite, but I'm switching languages and projects a lot, so it works. I mostly work in the terminal. But it's nice to be able to select a line or two and ask a focused question through the Copilot chat. For unclear reasons, the response time is way better through Copilot than through the CLI. Maybe it's a matter of how much they're sending? Not sure what else it could be.

If I have a more abstract or general question, I'll actually jump over to the desktop app and ask there. No need to clutter up my context window with long explanations. And that way they're saved with a nice name, in case I want to refer back to them.

For small changes (or small changes across a bunch of files), I'll let `claude` do its thing, then review the diff in the GitHub Desktop app.

For bigger stuff I usually start in planning mode (shift + tab). Worth noting that "planning mode" is not really a mode, it's just some text that gets added to the prompt; meaning that it's possible for Claude to forget that it should be planning, not executing. I've seen it happen, suddenly it's like "whoopsy doopsy, I changed your files!" So if not editing is important, I'll note that in my prompt, for extra weight.

By default, it stores the plans it makes in `~/.claude/` with a silly name. I usually tell it to create a plan and store it in my repo's `/docs/plans/` with a meaningful name. That way it's easier to keep track of over time. I'll commit it, then let `claude` update it as we proceed, then delete it when the work's done. Leaves a nice audit trail. Sometimes Claude will decide to make a list of steps and check each of them as it proceeds. Sometimes not. Whatever.

For various reasons, the work can get interrupted or go sideways. It's nice to have a file to restart from. And then I can ask Claude to review everything that's been done at the end and make sure all the details have actually been handled. Fucker's a bit ADHD, tends to wander off.

I'll usually do a bit of back and forth before I'm satisfied with the plan. I'll usually have it break the plan down into multiple phases, then tell it to start with the first phase, commit when its done, then wait for me to say its time to move on to the next.

Again, I'm usually looking at diffs as we proceed. Unless I notice it doing something weird or wrong, and I'll stop it and provide more instructions.

If it's a big, discreet chunk of work, I'll make a feature branch, go through it all as I just described, then make a PR so I can review it cleanly in its entirety.

I've tried using git worktrees (more on those below), but have found they're generally more nuisance than they're worth. You've got to inject env variables, copy over local settings, deal with conflicting ports, etc. Not worth it.

Also I've found that my brain gets pretty maxed out with two different streams of thought for the same project. Somehow it's much easier to switch contexts between projects than within a project. YMMV. But so I'm usually doing all this stuff with a few projects at once, and switching between them as things progress. This Claude's working on something? Let me check how that other Claude is doing. Etc.

As to what I'm doing more specifically, it really depends on the project, the language, the task. Sometimes I'm just using `claude` to give me ideas and feedback. Sometimes I'm writing tests and having it write implementation. Sometimes I'm using it to plan out big new chunks of work. Sometimes I'm having it crank on some mechanical chore.

## Todos

Don't be fooled by the todo system built into `claude`! It'll wipe your todos at the drop of a hat. Let it use them as its own task list, which it likes to do.

I make use of plans, as I described, and also keep a `todos.md` in the root of my repos. `claude`'s good about updating something like that once you get it going with the pattern.

## Context

You've got a context window. As you proceed, it fills up. The stuff in it gets sent to Claude with every prompt. So that's a lot of tokens right there. The more that's in your context, the less impact each new bit of text will have. So people typically recommend not filling it up, things can get wonky towards the end. (That path leads to AI psychosis.) Luckily, these days `claude` keeps about 40% of your context in reserve, and when you get to that point it auto-compacts everything that's happened so far. Meaning that the LLM analyzes the existing context and makes a summary of it, which then becomes the new context. I find all that works well, and I mostly don't think about it.

You can run `/compact` yourself at any point. More interestingly, you can give the compact command specific instructions: `/compact include new API details` or whatever is important to retain.

Use `/clear` to start a new session. (Poorly named, IMO, though it does indeed clear the scrollback.)

I always give my sessions names using `/rename`. Makes it easier to keep track of what I'm up to. `/resume` allows you to jump back into a session, or you can `claude --continue` from the command line to jump into the last one you were using. Seems to be per-directory or repo or something.

There's a million blog posts out there about "context engineering", if you want to get into the details. I don't, I just let it do its thing and it seems to work out okay.

## Rewinding

`esc + esc` allows you to rewind back to earlier points in the chat. Usually I use that if I mess up. If Claude messes up, rewinding's a mixed blessing, because you then have to give it new additional instructions to ensure it doesn't just do the same dumb thing again. It'll give you the option to rewind just the conversation or the conversation and the code; I find that the latter is hit or miss.

## Command line, git

In general, Claude's super good with the command line. But the specific commands it comes up with can be... idiosyncratic. Fucker _loves_ `sed`.

In some ways it's super good with `git`. I let it write commit messages all the time, it's great at that. But anything complex and I do it manually. I'm a big fan of `git add --patch`, which Claude can't handle at the moment due to its interactive nature. (Why not? Isn't it just more typing into the shell?) Simple rebases are fine, but if it gets tricky I take over. But I love `git` way more than a normal person should. YMMV.

Speaking generally, if you can do something via the command line, it's a good way to get `claude` to do it. It's shockingly good at writing bash scripts. So I'll often have it write up a script to do a thing, rather than winging it command by command. Like the plans, even if it's only around for a commit or two, it's nice to have the specific audit trail of what was going on. Again though, I like bash an unreasonable amount, so you might approach it differently. I've actually built up a pretty epic bash style guide, and I've got an associated skill (more on those below) that works well.

## Desktop / iOS app

I use the desktop and iOS apps quite a bit. (Often referred to as Claude Web, which is true enough, but also confusing, because each of the three - web, macOS desktop, and iOS - have different capabilities and quirks.)

As I said above, I use the desktop and iOS apps in regular chat mode to do general research. Ask a question, move on to something else, then come back a while later to find a nice essay waiting for me.

I also use code mode on them. This gets trickier.

Code mode on the iOS app is the simplest. It runs in a cloud environment, some VM that Anthropic runs for you. AFAIK, the only thing you can configure is how much network access the container has: none; the normal amount (which is fairly restricted); or all. I guess the default is "some" because who knows what you have in your repo, and maybe you don't to expose it all to the web. (Though personally I feel like exfiltration risks are minimal for the things I do.) But of course you shouldn't be storing secrets or PII or whatever in your repo anyway!

Regardless, Claude does a good job running in "normal" mode, but if you want it to be able to download dependencies and such, you've got to open it up.

Code mode on the iOS app tends to be much more hands-off. It doesn't ask you for permissions every ten seconds, it just runs. And when it's done, it sends you a PR. Nice and simple. You can, of course, continue the chat and have it update the PR. So for certain kinds of things it's fantastic: give it a task, let it rip, see what it comes up with. Repeat.

Code mode on the desktop app allows you to do all of that, plus you can run it in local mode. In which case it creates a worktree (stored in `~/.claude-worktrees/`). So that's kind of a nice in between ground. More autonomous than `claude` cli, but more real than the cloud environment. And it manages the worktree (to some degree, though the problems I mentioned above still apply), so that's easier than creating one manually and firing up `claude` in it.

I might jump over to the desktop app to have it do a spike on something. More specific and grounded than the kinds of general questions I'd ask the desktop chat, but not detailed work, necessarily.

## Dev containers

I haven't messed around with dev containers yet. For serious work, that seems like a good pattern. VSCode handles them for you, I'm sure other IDEs do the same these days. If you've got your code and your `claude` running in a container, you can use `--dangerously-skip-permissions` and really let it fly.

## Notifications

I've got some scripts that get triggered by `claude` hooks and notify me via the macOS notifications system when `claude` is done with a task, or waiting for input, or whatever. You can (and people do) take this further, get it to text your phone or whatever. This seems like a good balance for me.

## Linting, formatting, and so on

Automated linting etc. is crucial. If / once you've got it set up, tell Claude about it. In one of your `CLAUDE.md` files, in a skill, or in a prompt.

Watch out for Claude taking the easy way out. I changed a lint config the other day, asked Claude to fix all the errors, came back to the tab to find that it had carefully put `eslint-disable` directives in every spot that an error occurred.

## Skills and commands

Skills and commands are similar, but I much prefer the former. In both cases, you're giving `claude` a file from which it'll load just a couple summary lines, then when appropriate it'll load the rest of the file and act on it. So a nice context savings.

But I haven't found many cases where a slash command makes more sense than having a real script that I tell `claude` to run. If I'm doing something repeatedly and on my command, I usually want it to go down a certain specific way. For example, I played around with having a `/dev` command that would handle running and restarting a development server. But I actually don't want Claude thinking about that, exactly. I want it to do the right way, every time. And anyway, I'm not actually lazy enough (yet) that I can't just jump to another terminal and run `yarn dev` or whatever. Makes the logs easier to track, etc.

Skills, on the other hand, I like. In one of my projects, I've got one for `writing-documentation`, `writing-bash-scripts`, `committing-changes`, `updating-todos`, and so on. (Anthropic says to name them `<gerund>-<noun>`.) Mostly `claude` uses them at the right moments. If in doubt, I just say `Using the writing-bash-scripts skill, do blah blah`. Great way to standardize practices and styles, with minimal context overhead.

## MCP

MCP servers are overrated. They use up tons of context, and almost everything they do can be done by `claude` shelling out. For web stuff I like the `playwright` one, that's kind of magic. Claude will just fire up a browser and take a look at its own changes, it's wild. Other than that, I've stopped bothering.

That said, I do use the LSP servers when available for whatever language I'm writing. Which I think use the MCP protocol to communicate with `claude`. All of these things are installed via the `/plugins` command.

There's a new experimental setting that makes `claude` talk to the MCP servers via the command line. Which is kind of hilarious. The idea being that it knows it can do stuff, but doesn't keep the whole shebang loaded into context, it just shells out as needed. I haven't played with it yet. You set `ENABLE_EXPERIMENTAL_MCP_CLI=true` and that gives you "MCP-CLI" mode. [More info.](https://github.com/anthropics/claude-code/issues/12836#issuecomment-3629052941)

## Config

### owloops/claude-powerline

The budget settings below are a bit questionable. I took them from [a GitHub issue comment](https://github.com/Owloops/claude-powerline/issues/23). Supposedly `67.5` is the magic number for the "Max 5x" plan. But since the subscription plans have soft limits, not clearly defined ones, I'm not really sure how that's supposed to work.

`.claude/claude-powerline.json`:

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
