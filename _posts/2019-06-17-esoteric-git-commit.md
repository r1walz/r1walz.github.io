---
layout: post
title: "# Esoteric Teachings About Git Commit"
comments: true
description: "How you should organise commits, the right way."
keywords: "rohit, ashiwal, organise, git, commit, blog"
---

Hey Everyone!

Now that we know how to use git-commit and what commits are all about, we are ready to learn about some of the rules which will help us in efficient collaboration.

#### ### Commit Related Changes

A commit should contain changes related to only one topic like fixing two different bugs should enjoy their separate commits. Small, concise and scope-limited commits make it easier for other developers to understand the changes and review them.

#### ### Commit Often

Small and concise commits give the reviewers a "smaller" area to focus on which in turn helps them in better reviewing of the code. Moreover, it allows us to share more frequently with others thereby reducing chances of merge conflicts and also enabling easier integration.

#### ### Don't Commit Half-Done Work

As discussed in the last blog post, commit is a logical entity. It should be logically independent and should contain everything from related test to documentation. Also, we should split commit into smaller logical chunks for efficient collaboration. If we are tempted to commit half-done work because of the need for a clean working tree, we can use git-stash instead. Even if we are committing WIP commits for the sake of review we should remember to squash those commits before merging them into the main tree so that everything remains logically clean and clear.

#### ### Test Your Code Before Committing

Sometimes we do not wait for that code review tool to finish testing our code on all platforms and we push our code to the main branch only to know that the new code broke something. This is very wrong. We should try to test our code thoroughly. Only when it passes the test suite successfully, we should merge it into the codebase. As a simple rule of thumb: divide commits such that it passes the test suite successfully for each commit.

#### ### Write Good Commit Description

Begin with a commit message, a very short summary describing overall changes in less than 50 characters. You can also add the "area" of work in the commit message.

Next line should be a **blank** line followed by a commit description.

Commit description: or the body of commit should teach us about the motivation and need for the commit, i.e., the body should spread light on the "why" and "what" part of the changes. Use imperative present tense in your commit description as if you are dictating the codebase to do something. For example,

```
sequencer: use argv_array in reset_merge

Avoid using magic numbers for array size and index under `reset_merge`
function. Use `argv_array` instead. This will make the code shorter and
easier to extend.

Signed-off-by: Rohit Ashiwal <rohit.ashiwal265@gmail.com>
```

The body should be wrapped around 72 characters since it helps git-log to format it beautifully while displaying information about the commits.

##### ### Example 1

Here is an example:

```
feat: add Snackbar for loginSuccessful or loginFailed
```

The message does classify the commit as a feature commit but it is kind of redundant as it is implied that a commit will always bring a new kind of change. Also, the commit message has an area work but it can be better formatted as:

```
login: display login state information using snackbar
```

This is a better message as in it provides a clear area of work and more generic kind of information about the what was done.

##### ### Example 2

Let's have a look on another example:

```
cherry-pick/revert: add --skip flag

We are trying to implement git cherry-pick --skip for that I've
introduced sequencer_skip in the sequencer.c file which basically
calls rollback_single_pick and then, if there are still instructions
in todo file, sequencer_continue.
```

Commit message looks nice but the commit description is not good. It speaks more about "how" we are trying to achieve whatever we are trying to achieve (in this case adding --skip flag to cherry-pick and revert). A better commit message could be:

```
cherry-pick/revert: add --skip flag

git am or rebase advise the user to use `git (am | rebase) --skip` to
skip the commit. cherry-pick and revert also have this concept of
skipping commits but they advise the user to use `git reset` (or in
case of a patch which had conflicts, `git reset --merge`) which on the
user's part is annoying and sometimes confusing. Add a `--skip` option
to make these commands more consistent.
```

This is better because it clearly explains the motivation of adding --skip flag and why is there a need for this flag anyway. The commit description also dictates the difficulties currently faced by the users providing even more reason for this change.

---

Now you know about the secrets of committing to achieve effective open source collaboration. Bring these rules in practice and you'll notice differences, be it in surfing the git history or cherry-picking the required commits just by reading the oneliners. Hope you learned something new!

Thanks!
