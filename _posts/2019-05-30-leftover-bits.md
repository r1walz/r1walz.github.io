---
layout: post
title: "# Leftover Bits"
comments: true
description: "Status of my pull request and hints about some small projects."
keywords: "rohit, ashiwal, gsoc, 2019, git, left, over, bits, blog"
---

Hey Everyone!

We are in the middle of the release of git v2.22.0 and everyone here is quite busy. The previous week ended with a lot of discussion about where to split the commits and coding guidelines and finally, now my pull request is in a position to be sent to the mailing list. I've thought to send my patch to the mailing list once things are calmer. But you can get exclusive early access [here][1] ;)

While developing software of this level, we are bound to find an obscure code which might lead to confusion and there we end up catching one such [piece][2]. So, I thought why not write a blog on fantastic bugs and where to find them? I will release that sooner than you know.

For once, I want to talk about what I'm leaving behind in this pull request. The scope of this PR is limited to \-\-skip option for cherry-pick and revert. But while working on it, I introduced a new member to `sequencer_*` family `sequencer_skip` which, as the name suggests, skips the commit and continues with the sequence. Now for it to be more "generic", we should also be using it to skip commits when using interactive rebase [[^1]] which is currently directly calling the required functions. This could really be a nice `good first issue` if you want to start contributing to git. Of course, this is the story if my patch gets merged. (0_0)'

I can't just waste my time doing nothing you know so I have decided to work on the next phase of the proposal, i.e., look for the flags that are present in am-based rebase but not in interactive rebase and implement them in the latter. According to what [Elijah suggested][3], `--ignore-whitespace` should be the easiest to port, ergo, I'm going to see into the code how I shall implement it in the interactive machinery and for that, I'm currently looking into the code for [git-apply][4].  The code is huge! @_@ How I end up here? Basically, rebase sets up am which in the end calls apply to apply whitespace fix and other tasks. It's a passing the parcel between these. Let's see what can I come up with!

Adios!

---
Footnote:

[^1]: 1: Since interactive rebase is closely related with cherry-pick and revert internally.

[1]: https://github.com/r1walz/git/pull/1
[2]: https://github.com/gitgitgadget/git/issues/230
[3]: https://public-inbox.org/git/CABPp-BEdgSHGTkUcg_UDRu50Ag+cCqigmvU4_JaRZRnDpgWcdA@mail.gmail.com/
[4]: https://github.com/git/git/blob/master/apply.c
