---
layout: post
title: "# The Final Report"
comments: true
description: "Final report that I submitted for GSoC 2019"
keywords: "rohit, ashiwal, gsoc, 2019, git, final, report, blog"
---

Hey Everyone!

My project was to [improve the consistency of sequencer commands][1]. There are two backends available for rebasing, viz, the am and the interactive. Naturally, there shall be some features that are implemented in one but not in the other. The project aimed to remove inconsistencies in how the command line options are handled. A copy of my project proposal is hosted [here][2]. The project was done under the guidance of [Thomas Gummerer][3] and [Elijah Newren][4], two of the best Git developers.

_Let's dive into my journey of GSoC with Git!_

## ## Pre-GSoC Period

I started contributing to Git from this February where Dscho (aka Johannes) was mentoring me to remove an [external dependency][5] of the MinGit package.

After some time, [I introduced myself][6] to Git where I picked a [micro-project][7] and continued working on it and improving my understanding of the mailing list. People at Git are extremely co-operative and the community is always active to help you 24x7. It’s the time when I received some critical reviews and learned how things work in an organization. The interaction taught me the workflow and more importantly how important “word choice” is when committing.

After several iterations and help from the people, I was able to complete my proposal that I finally submitted for GSoC ‘19. And yeah! I was selected for GSoC!

## ## The "Plan"

I planned on completing the following tasks:

```md
1. Suggest relevant flags for operations that have such a concept like git cherry-pick --skip
2. Unify the suggestive messages of git (cherry-pick|rebase-i) with git (am|rebase)
3. Implement flags that am-based rebases support, but not interactive, in interactive rebases, e.g.:
	--ignore-whitespace
	--committer-date-is-author-date
	--ignore-date (aka --reset-author-date)
	--whitespace=...
4. [Bonus] Make a flag to allow rebase to rewrite commit messages that refer to older commits that were also rebased
5. [Bonus] Performance run on different backends of rebasing, if everything agrees, deprecate am-based rebases
```

Alas! I was only able to complete the first two tasks and flags \-\-ignore-whitespace, \-\-committer-date-is-author-date and \-\-ignore-date with almost no work done on \-\-whitespace=... flags and [Bonus] features.

## ## Phase 1

The phase started with [teaching cherry-pick and revert to "skip" commits][8]. git am or rebase advice user to use git am \-\-skip or git rebase \-\-skip to skip the commit that has become empty or has risen conflict. OTOH, git rebase -i or cherry-pick advice user to use git reset HEAD which on the user’s part is annoying and sometimes confusing. My PATCH brought consistency between the advice of these commands by introducing \-\-skip option to these subcommands.

## ## Phase 2

Most of the work was done in phase 2. I started by [implementing and  polishing][9] \-\-ignore-whitespace and \-\-committer-date-is-author-date flags. The former was expected to appropriately handle whitespace changes while committing while the latter helped us to set the committer date equal to the value same as the author date. This was the time when I got familiar with the internal workings of the sequencer. I sent the patches for review while I started working on another flag \-\-ignore-date. Review took a long time (Git community as always on their toes to only allow the most pristine code into their tree). By the time of phase 3 I was only able to work on these two flags :/

## ## Phase 3

The [parallel submission][9] of the previous (two) patches was causing a mental mess, so I switched a new topic [rebase-i-more-options][10]. It contained the previous patches along with the code of yet another flag \-\-ignore-date (also aliased \-\-reset-author-date). Since the polishing from phase 2 took a toll on time, I asked my mentors if we can start working on \-\-whitespace=... flags while my patches were still in review to which they answered, "It's fine even if we are not able to meet all the goals, what's important is that we only allow well-tested and well-written code into the git's source". I agreed. I spent all my time in this phase to polish the patch series which was sent to the mailing list.

## ## Post-GSoC

The project still requires the following to be done:

```md
1. Introduce --whitespace=... flags
2. Work on the aforementioned bonus features
```

I am planning on continuing even after GSoC. I'll take the project to completion since I feel responsible for all the projects that I'm part of.

Best Wishes  
Rohit

---
#### ### git log

The following commits were sent during GSoC '19 and they are currently present in git/git's tree (master and proposed updates).

[ac9e40e8ef](https://github.com/git/git/commit/ac9e40e8ef) Merge branch 'ra/t3600-test-path-funcs'
```
A GSoC micro.

* ra/t3600-test-path-funcs:
  t3600: use helpers to replace test -d/f/e/s <path>
  t3600: modernize style
  test functions: add function `test_file_not_empty`
```

[d97c62c828](https://github.com/git/git/commit/d97c62c828) Merge branch 'ra/cherry-pick-revert-skip'
```
"git cherry-pick/revert" learned a new "--skip" action.

* ra/cherry-pick-revert-skip:
  cherry-pick/revert: advise using --skip
  cherry-pick/revert: add --skip option
  sequencer: use argv_array in reset_merge
  sequencer: rename reset_for_rollback to reset_merge
  sequencer: add advice for revert
```

[966fc12521](https://github.com/git/git/commit/966fc12521) Merge branch 'ra/rebase-i-more-options' into pu
```
"git rebase -i" learned a few options that are known by "git
rebase" proper.

Looking good.

* ra/rebase-i-more-options:
  rebase: add --reset-author-date
  rebase -i: support --ignore-date
  sequencer: rename amend_author to author_to_rename
  rebase -i: support --committer-date-is-author-date
  sequencer: add NULL checks under read_author_script
  rebase -i: add --ignore-whitespace flag
```

---
Psst!

I also have a [repository][11] containing all the patches that I have sent (and will be sending) to the GIT mailing list. The work done under GSoC contains [GSoC] tag in the commit message. Clone the repo and use `git log --grep="GSoC"` to list all "GSoC" commits.

---
#### ### Special Thanks

I'd love to take some time and thank all the people who helped me to realize the project, especially:

```md
- Christian Couder
- Elijah Newren
- Eric Sunshine
- Johannes Schindelin
- Junio C. Hamano
- Phillip Wood
- Thomas Gummerer
```

and many others. Thank you very much!

[1]: https://summerofcode.withgoogle.com/projects/#6407042053439488
[2]: https://rashiwal.me/git_proposal_19.pdf
[3]: https://www.linkedin.com/in/thomas-gummerer-47715a15
[4]: https://www.linkedin.com/in/elijah-newren-0a41665/
[5]: https://github.com/git-for-windows/git/issues/1970
[6]: https://public-inbox.org/git/CAL7ArXqkVfrnQWYFDYdwMGkZjHCwzyQX4pbKCo=KCzy-zJiRBw@mail.gmail.com/
[7]: https://public-inbox.org/git/20190303122842.30380-1-rohit.ashiwal265@gmail.com/
[8]: https://public-inbox.org/git/20190608191958.4593-1-rohit.ashiwal265@gmail.com/
[9]: https://public-inbox.org/git/20190712185015.20585-1-rohit.ashiwal265@gmail.com/
[10]: https://public-inbox.org/git/20190806173638.17510-1-rohit.ashiwal265@gmail.com/
[11]: https://github.com/r1walz/git-patches
