---
layout: post
title: "# Common Teachings About Git Commit"
comments: true
description: "How to use git-commit."
keywords: "rohit, ashiwal, organise, git, commit, blog"
---

Hey Everyone!

I know Git (a popular [VCS][1]) can be intimidating at first but learning and understanding it can help us efficiently develop software solutions. Today, I'll introduce you to "commit", a very commonly used command, which is linked to the very concept of version control.

## ## git-commit

According to [man page][2] of git-commit:

> git-commit - Record changes to the repository
>
[\-\-\- and a long description \-\-\-]

Well, that is not very helpful to beginners. Man pages can be hard to understand (or even navigate through) by themselves. Let's break down to simpler terms what git-commit is all about.

> quick note: we are not talking about commits as in git-internals but as an entity for the better understanding since users will not be going inside and question us anyway :p

A commit is a logical entity which records a snapshot of the current state of the file system. It contains information about which files were changed, who authored them and at what time, time of commit, who committed (to the main tree), a message suggesting what was done/changed and why, a PGP signature and much more in a cryptic form.

git-commit is the porcelain command which records these commits to the commit tree and updates the HEAD of the branch to point to the latest commit. Prior use of the git-add [[^1]] command is required to select the changes that will be staged for the next commit. Then git-commit is used to create a snapshot of the staged changes along a timeline of a Git project's history.

### ### Important Options

```
-m <message>  :  Sets the commit's message. A oneliner describing what
                 the commit is all about
-a, --all     :  Includes all currently modified (and tracked) files
                 in this commit
--amend       :  Rewrite the last commit with any currently staged
                 changes and/or a new commit message
--no-edit     :  Do not launch the editor, just use the previous commit
                 message
-S[<keyid>]   :  Add your PGP signature. Remember to add a signing key
                 using git-config for easier workflow
-s            :  Add DCO at the end of commit description
```

### ### Usage Examples

For a basic workflow, you can use git-add command to stage changes for the next commit.

```
$ git add main.c
$ git commit -m "add the driver program"
```

If you have lots of changed files in your working directory and want all of them included in the next commit then make use of `-a` option. Thereby omit the `git-add` step.

```
$ git commit -am "teach this that"
```

The `--amend` option comes handy when we have to change that mistyped word in the commit message/description or forgot to add that header file.

```
$ git add forgotten-header.h
$ git commit --amend [--no-edit]
```

You can also PGP sign your commits using `-S` option or add a simple DCO [[^2]] to your commits using `-s`.

```
$ git commit -sS
EDITOR -------------------------------------------------------------------------
main: add greetings                                           # commit message

We need to greet our users before giving the control to the   # commit
CLI interface. Add greetings at the startup of the program.   # description

Signed-off-by: Rohit Ashiwal <rohit.ashiwal265@gmail.com>     # DCO

# Please enter the commit message for your changes. Lines starting
# with '#' will be ignored, and an empty message aborts the commit.
#
# On branch master
#
# Initial commit
#
# Changes to be committed:
#       new file:   main.c
--------------------------------------------------------------------------------
```

## ## Summary

We learned about what commits are and how to record changes using git-commit. We also learned some common options of the command. But only knowing about what they are is not enough. There is much more to it like how should we organise commits, i.e., how to divide them properly, what to write in commit message/description. Even length of each line of commit message/description is important! Soon I'll write another blog explaining about these points.

See you there!

---
Footnote:

[^1]: 1: Here is a tutorial on [basics of Git][3] with examples
[^2]: 2: What is [DCO][4]? Word of [DCO][5].

[1]: https://www.git-tower.com/learn/git/ebook/en/desktop-gui/basics/what-is-version-control
[2]: https://git-scm.com/docs/git-commit
[3]: https://rubygarage.org/blog/most-basic-git-commands-with-examples
[4]: https://en.wikipedia.org/wiki/Developer_Certificate_of_Origin
[5]: https://developercertificate.org/
