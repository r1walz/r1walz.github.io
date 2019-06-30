---
layout: post
title: "# First Evaluation"
comments: true
description: "The First Evaluation."
keywords: "rohit, ashiwal, gsoc, 2019, git, first, evaluation, blog"
---

Hey Everyone!

We are on a path to implement --committer-date-is-author-date in rebase -i and this week I got to explore some parts of it, particularly the sequencer file. It is clear from the code that not only the functions directly spawning "git-commit" can be "fixed" by setting GIT_COMMITTER_DATE variable but also some functions like commit_trees() which check for env variables will be fixed through this way. Moreover, I found that we _might_ need to change the merge mechanism code to handle the flag but more research is needed.

## ## Other Stuff

![first_evaluation](/assets/first_evaluation.png)

The results of GSoC first evaluation was out and I passed!
