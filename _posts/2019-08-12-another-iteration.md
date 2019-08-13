---
layout: post
title: "# Another Iteration"
comments: true
description: "Story of another iteration submitted of the previous patch"
keywords: "rohit, ashiwal, gsoc, 2019, git, another, iteration, blog"
---

Hey All!

Sorry for a late post. Weeks are busy as we are in the middle of our internship season. I had to run between things and this is the time which I'm able to factor out of my schedule.

Last week was spent polishing the [patch][1] that I sent. From making the patch compile on Windows to factoring out code to changing documentation,  I had accounted for all the suggestions that I received there. The [PR][2] which focused on adding \-\-ignore-date to the interactive machinery was also added to the series. There was nothing new to the logical part, just changing the control path and introducing functions.

We are in the final week of GSoC now and I still yet to implement the \-\-whitespace=\<...> flags. I'll try to, at least, form a minimal patch (or idea) of how these new set of flags should work. I may not be able to implement in the given time, but GSoC is not about completing the project, it's about introducing a student to the world of open source. And now that I am familiar with the code of git, I'll become a "serial" committer and will try to keep my project alive until completion.

See ya!

[1]: https://public-inbox.org/git/20190806173638.17510-1-rohit.ashiwal265@gmail.com/
[2]: https://github.com/r1walz/git/pull/4
