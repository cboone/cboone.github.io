---
date: 2026-01-15T11:48:04-05:00
sections: ["tools"]
title: "git diff: zdiff3"
---

I've been using `git` since 2007 or so, when the pre-GitHub team started talking it up in [the SF Ruby scene](https://web.archive.org/web/20070216143617/http://sfruby.org/). (Oh man, icanhazRuby. That was a time.)

I've always found the merge conflict resolution text to be a bit confusing. Who's us and who's them? What exactly happened here? TIL that part of the problem is that, like a fool, I've left the `merge.conflictstyle` config setting on its default `merge` value.

For years now, the better choice has been `diff3`. That setting makes it so the merge conflict resolution text in your file includes the original text content along with the two conflicting versions. Thus you can at least see the context of the change, rather than trying to remember or guess what the changes were about in the first place.

Even better, since 2022 (`git` version 2.35), there's been a third setting option: `zdiff3`. Which not only includes the original context of the changes, but pulls out overlapping, similar content from each of the changes. Thus reducing the amount of conflict you need to think about.

This all sounds a little abstract, I realize. The short version:

In your `.gitconfig`:

```gitconfig
[merge]
  conflictstyle = zdiff3
```

For more detailed information (including nice visuals), see [this post](https://www.ductile.systems/zdiff3/) and [the `git` docs](https://git-scm.com/docs/git-merge.html#_how_conflicts_are_presented).

{{< notice info >}}
Recently I found [this amusing interview](https://web.archive.org/web/20070216143357/https://sfruby.org/posts/interview-with-the-san-francisco-rubyists-at-lingr) Chris Wanstrath did with me and [Danny Burkes](https://github.com/dburkes) in early 2007, well before any of us were using `git`. Note the CVS / SVN joke. Also, I retract my statement about Poison; Danny was right, [Def Leppard rules](https://m.youtube.com/watch?v=nhSdljm909Y&pp=0gcJCTIBo7VqN5tD).
{{< /notice >}}
