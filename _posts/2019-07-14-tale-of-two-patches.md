---
layout: post
title: "# A Tale of Two Patches"
comments: true
description: "A blog on --ignore-whitespace and --committer-date-is-author-date of rebase -i."
keywords: "rohit, ashiwal, gsoc, 2019, git, interactive, rebase, blog"
---

Hey Everyone!

This week was very productive. I solved the part where we were spawning an octopus. It turns out that it also checks for the "GIT_COMMITTER_DATE" env variable and that reduced the work to a child's play.

_For perfectionists, here is the full flow chart:_

![flow chart showing control flow](/assets/images/committer-date-is-author-date-2.png)

Finally, I was able to send two patches for the review, [here][1] and [here][2]. Merging them will teach the interactive rebase the art of ignoring whitespace changes and lying about the committer date (by changing it to the author date). Since the patches were dependent on each other, in essence, they had overlapping codes, I had to base my second patch on the first. Because they were sent during weekends, they didn't receive any comments yet. But believe it will soon receive their critical eye soon.

## ## Future Plans

My college will re-open very soon, but I don't think that will hinder me from my work at Git. Workflow at Git allows even a busy student to work on his project without any (say) "delays" since the community is spread across the globe, we are sure to receive the reviews 'round the clock.

I'll start working on \-\-ignore-date flag which will help us "lie" about the author date by ignoring the date author date in the patches and using the time of commit. Actually, I've already started working on this and soon will submit a draft PR on GitHub.

Stay Tuned!

[1]: https://public-inbox.org/git/20190712185015.20585-1-rohit.ashiwal265@gmail.com/
[2]: https://public-inbox.org/git/20190712185357.21211-1-rohit.ashiwal265@gmail.com/