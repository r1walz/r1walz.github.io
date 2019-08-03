---
layout: post
title: "# The Discussion"
comments: true
description: "The Discussion on justifying reading author_script from disk is safe."
keywords: "rohit, ashiwal, gsoc, 2019, git, discussion, author, script, reading, safe, blog"
---

Hey Everyone!

As mentioned in the last week's [post][1], Junio pointed out that calling read_author_date_or_die() (now, read_author_date_or_null()) _might_ be unsafe as we _might_ not have a saved copy of the author information on the disk.

The mentors and I had a long discussion on how the current calling of function is actually "safe". Here is the thought process:

1. do_pick_commit() and do_merge() always call write_author_script() to write author information to the disk before calling run_git_commit() so, we are sure to find the information there on the disk.
2. commit_staged_changes() only calls run_git_commit() when it is stopped because of merge conflicts or by 'edit' todo commands. In this case, author_script is already written by the previous invocation of git. In all other cases, run_git_commit() throws an error as it should. So we are fine if read_author_date_or_null() also throws an error.

## ## Current Work

I am working on polishing my patches. The work is already done but before sending them to the mailing list I am thinking of updating my [PR about introducing \-\-ignore-date][2].

If everything goes well, I'll have it done by tomorrow evening and will send all the commits under a new common topic "rebase-i-more-options" (Junio named it :p) by Tuesday.

See ya!

[1]: https://rashiwal.me/2019/second-evaluation/
[2]: https://github.com/r1walz/git/pull/4
