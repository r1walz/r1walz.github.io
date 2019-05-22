---
layout: post
title: "# To Pick Or Not To Pick"
comments: true
description: "A journey add --skip to cherry-pick."
keywords: "rohit, ashiwal, gsoc, 2019, git, cherry, pick, blog"
---

Friends, Romans, countrymen!

Last week was quite busy. Shifting rooms and doing paperwork is a tiring affair. After I was ***free()***d, I contacted my mentors over the e-mail to know what should my next move be. They gave me two ways to proceed:

1. Familiarize myself with the mailing list and work-flow at Git, or
2. Get started with the coding part.

Thanks to the people at Git [[^1]] and [micro-project][1] that I did during the pre-GSoC period, I already knew how things are. So naturally, we agreed that I should code.

## ## Planning

According to the [proposal][2] that I sent over to Git, I should start by implementing flags for operations that have **such a concept**, _e.g._, `--skip` flag for cherry-pick, and so I did.

What does git [cherry-pick][3] do, you say? Well, according to Git,

> cherry-pick: apply the changes introduced by some existing commits

Cherry-picking is basically choosing commits (from any \<remote>/\<branch>) and applying them to the current branch. So, what should ---skip flag do?

> ---skip: skip current commit and continue 

The idea is to skip the commit which was "picked" and continue applying other commits. There could be many reasons to drop that commit including but not limited to merge conflicts, commit becoming "empty" due to conflict resolution, etc.

## ## Implementation

On the inside, what I actually mean by skip is resetting @ (aka HEAD) to where it was before the merge and continuing (if there are still instructions left in todo [[^2]] file).

Here is the snippet which exactly does the same. It is from the initial stages of the operation: add skip [[^3]]. We are spawning `git reset --merge` to reset our HEAD and then calling `sequencer_continue()` to continue.

```c
int sequencer_skip(struct repository *r, struct replay_opts *opts)
{
	struct child_process reset = CHILD_PROCESS_INIT;
	reset.git_cmd = 1;

	argv_array_push(&reset.args, "reset");
	argv_array_push(&reset.args, "--merge");

	run_command(&reset);

	if (file_exists(git_path_seq_dir()))
		sequencer_continue(r, opts);
	
	return 0;
}
```
Furthermore, to account for this addition of the new flag, we have to change advice messages to instruct user take appropriate action, but doing so, will also break some test because they depend on the output (advice message).

Adding more test and documentation will finish the process of adding this new _cool_ flag to cherry-pick's arsenal.

## ## Motivation

git am or rebase advice user to use `git am --skip` or `git rebase --skip` to skip the commit that has become empty or has risen conflict. OTOH, git `rebase -i` or `cherry-pick` advice user to use git reset HEAD which on the user's part is annoying and sometimes confusing. My **[PATCH]** will bring consistency between advices of these commands that will remove the confusion that may arise.

Thanks for reading!

---
Footnote:

[^1]: 1: Great people like dscho, \_ikke_, rafasc, abngrn, always availabe on #git-devel, freenode
[^2]: 2: File of instructions that sequencer commands create to keep track of what should they do next
[^3]: 3: For lurkers out there, [here][4] is the link of my pull request

[1]: https://public-inbox.org/git/20190303122842.30380-1-rohit.ashiwal265@gmail.com/
[2]: https://drive.google.com/file/d/1qEVEtfXPAubpF99wvPybxoT6QNtvG6OI/view
[3]: https://git-scm.com/docs/git-cherry-pick
[4]: https://github.com/r1walz/git/pull/1

