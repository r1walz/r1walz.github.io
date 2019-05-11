---
layout: post
title: "[RFC] Git Intro"
comments: true
description: "My thoughts on selection to GSoC '19 with Git."
keywords: "rohit, ashiwal, gsoc, 2019, git, introduction, blog"
---

Hello everyone

It's the high time of the year when an **open-source**rers [[^1]] magical prowess is at their highest. Yes, GSoC is 'round the corner and everybody is trying their very hard to get selected in their favourite organizations.

***git-a-chu! I choose you!***

I started contributing to Git [[^2]] from this February where Dscho [[^3]] was mentoring me remove an [external dependency](https://github.com/git-for-windows/git/issues/1970) of the MinGit package. Dscho is a very friendly guy and especially helpful to beginners. He explained to me every detail, whatsoever I needed, to solve the problem in hand and it is because of his guidance I was able to fix the issue.

I was almost heart-broken when he revealed that [git-for-windows](https://gitforwindows.org/) is not coming in GSoC '19 as the people at Git (who applied as mentors) are not exactly "windows" person. But I continued solving more issues for git-for-windows.

After some time, I [introduced](https://public-inbox.org/git/CAL7ArXqkVfrnQWYFDYdwMGkZjHCwzyQX4pbKCo=KCzy-zJiRBw@mail.gmail.com/) myself to Git where I picked a [micro-project](https://public-inbox.org/git/20190303122842.30380-1-rohit.ashiwal265@gmail.com/) and continued working on it and improving my understanding of the mailing list. People at Git are extremely co-operative and the community is always active to help you 24x7. It's the time when I received some critical reviews and learned how things work in an organization. The interaction taught me the workflow and more importantly how important "word choice" is when committing.

Almost a month has passed and my micro was accepted into the Git's master branch. Now was the time when I should start working on my [proposal](https://public-inbox.org/git/20190322151157.9550-1-rohit.ashiwal265@gmail.com/). My project deals with ***improving consistency of sequencer commands***. as there are still some inconsistencies among these commands, e.g., there is no `--skip` flag in `git-cherry-pick` while one exists for `git-rebase`. Successful completion of this project will remove inconsistencies in how the command line options are handled.

After several iterations and help from the people, I was able to complete my proposal that I finally submitted for GSoC '19. During the buffer period, I could do nothing but wait since my examinations were going on which were keeping me busy. After everything was over, the results of GSoC were closing in and I received the following mail.

---
On Tue, 7 May 2019 03:59:10 -0700 Thomas Gummerer \<[t.gummerer@gmail.com](mailto:t.gummerer@gmail.com)> wrote:

> Hi Rohit,
>
> Congratulations again on getting accepted to work on Git in this year's Google Summer of Code.

Thank you for this great news! I am glad and excited to work on the project
with Git. I thank Git for selecting me and providing such able mentor to
mentor me and hopefully leading the project towards completion.

And thus my journey to improve Git began.

Best <br>
Rohit

---
Footnote:

[^1]: 1: **Open source** (_adjective_): software for which the original source code is made freely available and may be redistributed and modified.
[^2]: 2: Git is a distributed version-control system for tracking changes in source code during software development.
[^3]: 3: Dscho, aka Johannes Schindelin \<[johannes.schindelin@gmx.de](mailto:johannes.schindelin@gmx.de)>, my first mentor and the best man I met at #git-devel
