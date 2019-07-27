---
layout: post
title: "# Second Evaluation"
comments: true
description: "The Second Evaluation."
keywords: "rohit, ashiwal, gsoc, 2019, git, second, evaluation, blog"
---

Hey Everyone!

Last week I sent two patched introducing --ignore-whitespace and --committer-date-is-author-date to the interactive rebase. Both received good reviews and I think --ignore-whitespace is in a better condition now.

As for the other, I still need to get some work done. I modified the function read_env_script() to accept NULL arguments to selectively retrieve the required information. Also, I introduced read_author_date_or_die() to read the author date from disk using that modified function. The thing is, there are three callers of run_git_commit (which calls our baby function) and it turns out, as Junio pointed, calling them might not be safe as we might not have a saved copy of the author information on the disk. I'm currently working on fixing this. This will significantly change the current implementation.

Phillip Wood mentioned that read_author_date_or_die() is not a good function, in essence, it kills the process in the library code. We try hard to keep the process from dying in a dirty state. So, it's better to give out an error and let the repo come to a "clean" state than error and die out. A piece of nice advice to keep in mind.

## ## Other Stuff

**College** Internship season is around the corner, so I had to spend some time with the Training and Placement team of the college to get my resume verified. This _long_ process kept me busy for the whole week! Other than that:

![secone_evaluation](/assets/second_evaluation.png)

The results of GSoC second evaluation was out and I passed! The project is going in the right direction and that too pretty fast (compared to other projects in the past), hope all my patches get merged unifying behaviour of different sequencer commands.

Best!
