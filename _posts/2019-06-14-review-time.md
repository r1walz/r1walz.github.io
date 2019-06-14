---
layout: post
title: "# Review Time"
comments: true
description: "How my review is going on."
keywords: "rohit, ashiwal, gsoc, 2019, git, review, time, blog"
---

Hello Everyone!

Last week was dull, I had no progress with coding. But I sent my first patch to the Mailing List for the review. [Find it here][1]. People, as usual, are very good at criticizing and reasoning. I have received a lot of constructive feedback on my patch. Having sent three iterations, there is still scope for improvement. These numbers do not matter when it comes to constructing a _nice_ patch.

About my week, I spent the majority of the amount of time tending to the requests of the mailing list and refining my next patch, introducing \-\-ignore-whitespace to rebase -i. Progress of the latter can be [tracked here][2].

## ## A  NEW Flag!

I am thinking of starting to work on the next flag, i.e., \-\-committer-date-is-author-date, yeah, I know that's a mouthful. What does it do? Basically, there are two types of dates which are linked to a commit \-\- Committer date and Author date. Author date is the date on which the commit was first recorded whereas the committer date is the date when the commit was modified (or the patch was applied). It might appear, at first, that they are the same, but they are not!

This sweet _little_ flag helps us "lie" 'bout the committer date. This basically sets the committer date to be equal to the author date and that's it.

### ### Implementation

\-\-committer-date-is-author-date is adapted from the flag with the same name which is available for git-am. For the am, the flag internally calls to setenv which sets the environment variable `GIT_COMMITTER_DATE` to the value of author_date (if \-\-ignore-date was not given else to an empty string). For the interactive rebase, I don't know for now, I am still reading the code. But some ways to handle this may be:

1. Just call setenv as we are doing for am
2. Introduce \-\-committer-date-is-author-date in the git-commit command itself [[^1]] and wire that to the rebase's flag.
3. Something else (0.0)?

If the first way works fine then the work would be drastically reduced to just five statements at most (0_0)' Second could be a bit tedious to do as it may spur heated discussions on the mailing list. Also, it might require me to study the code of git-commit from bottoms up which is a tiring affair in itself. Let's see how things unfold.

'Till then, bye!

---
Footnote:

[^1]: 1: Well, git-commit already has \-\-date flag so, it may just require some re-wiring

[1]: https://public-inbox.org/git/20190608191958.4593-1-rohit.ashiwal265@gmail.com/
[2]: https://github.com/r1walz/git/pull/2
