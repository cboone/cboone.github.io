---
date: 2026-03-06T14:51:36-05:00
sections: ["llms"]
title: "Scale of Vibes"
---

This is my personal reference scale for categorizing my projects. It's intended to give a sense of what the balance of LLM to human is on one of my projects. This covers everything from IDE autocomplete to CLI harnesses to the Claude Code app on my phone to GitHub Copilot PR reviews. So LLM is a vague term here meaning any kind of tool that talks to an LLM-backed API.

This is only about the technical parts of software projects. Refer to [my AI Transparency Statement](/about/ai-transparency-statement/) for more general details on my use of LLMs.

And none of this is clearly defined or clearly delineated; it's vibes, after all. This is just a rough attempt at conveying what went into a piece of work. In reality, most of my work overlaps multiple of these levels, different pieces of the work fall in different categories, and an individual area of work might bounce back and forth between levels as the work progresses.

That said, a rough idea seems better than no idea.

## 0. No Vibes

_Caveman style._

Not even LLM-assisted autocomplete. I haven't worked like this in many months. I have some personal projects that qualify as No Vibes, due to their age, but I don't think any are public.

Of course, it's been so many years since I've coded without some kind of autocomplete and always-on easy access to internet search I'm not even sure I could do it. I wrote my first public Rails app (in 2004) in the passenger seat of a car on a road trip, flipping through Dave Thomas's pickaxe book, no internet access for days. That might have been the last time I coded truly unassisted.

## 1. Human Work, LLM Assisted

_Aka work._

Fancy autocomplete reading my mind with its next edit prediction. Asking the in-IDE LLM chat for explanations of what's going on, or why a bug isn't responding to my ministrations, or what would be a more idiomatic way to write some code, etc. Using the LLM

## 2. Human + LLM Work Blended

_Still getting my hands dirty, but mostly for fun._

Back and forth, them and me.

## 3. Human Micromanaged LLM Work

_Dreaming of code._

I don't write any code in the sense of, you know, writing code. But level 3 involves a lot of reading of code, and giving detailed feedback, and managing the interaction of multiple LLMs providing feedback to each other. In level 3, the LLMs are writing the code, but I'm still reading most of it and guiding it in various detailed ways. The LLM creates the detailed execution plan based on the details I provide.

## 4. Human Directed LLM Work

_Human proposes, LLM disposes._

I have an idea, but at a high level or missing some important details. I'll ask an agent to look into it, figure out what's possible, and come back with a plan. If the plan seems reasonable, I let it rip.

For me, this is most often prototypes, small tools, one-offs, spikes on existing projects, or just uninteresting work. Often done via the Claude Code iPhone app. It's very hard to get any kind of interactive work done with Claude through that interface (in fact they've optimized it to work independently, without needing oversight or permission), so this is level is often the simplest way to approach a problem, even if I intend to rework it with more involvement later.

I suppose large, high-level plan generation might fall here too. I'll talk through an idea at a very high level, then let the agent create a multi-phase plan. The execution of the phases

## 5. Max Vibes

_All LLM, no human. What is this code you speak of._

For me this is when I ask Claude, say, a question about something, look away for a bit, and come back to find an entire app written and ready to go. Level 5 involves little to no creativity on my part, and the only work I put in is figuring out what the new thing even does and how to use it.

I don't think any of my experiences with level 5 have seen the light of day. Except for twice when I asked Claude to investigate a bug on a forked repo and came back to discover that the bug had been identified, fixed, and there was now an upstream PR with my name on it. In one case the first I learned of this was when the PR was approved and merged.

What I learned from _that_ experience is that if you use any of GitHub's tools to clone a forked repo, you wind up with one remote: the upstream repo. And if you tell Claude to work in a repo configured like that, it thinks submitting upstream PRs is the right thing to do. Lesson learned. (Luckily in both cases the fixes were tiny and good.)
