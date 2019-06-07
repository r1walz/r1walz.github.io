---
layout: post
title: "# Ignoring Spaces"
comments: true
description: "Teaching rebase -i to use --ignore-whitespace."
keywords: "rohit, ashiwal, gsoc, 2019, git, interactive, rebase, blog"
---

Hello!

How fast last week went by, I can't tell you! A lot of code reading and it turns out we already have a flag that does the job. As I said in my last post, I went deep into the code for git-apply only to find out that there exists a merge strategy "ignore-space-change" which, more or less, does what we require. Although there are some edge cases that I'll mention in my cover letter which need to be taken care of in a separate patch.

## ## New Plan

Since we already have this merge strategy, our job has reduced to translate "--ignore-whitespace" to "--strategy-option ignore-space-change" within the code. I have tried to do the same, you can see that in this [PR][1].

## ## Other Stuff

Learning is a phase that never ends. We can learn things as we grow and proceed. And even as I continue on this journey, I am getting important tips from my mentors that may have missed otherwise. These tips are valid even for other programming projects, not git in particular. For example, when to free memory and why? Using APIs and design patterns. I thank them to patiently answering even my stupidest questions.

Something interesting happened in the last week ;) Google sent an invitation for the **foo.bar** challenge to me! Naturally, I accepted the challenge. According to [Quora][2]:

> **Google** uses a secret web tool called **foo.bar** to recruit new employees based on what they search for online. Specific searches relating to coding and software development prompt **Google** to ask the user if they are "up for a challenge" in a system which recently landed a college graduate a job at the company.

So, wow! It is a 5 level challenge and I'm currently on level 3. Who knows I might fetch an internship at Google @_@. Let's hope for the best!

See-ya!

[1]: https://github.com/r1walz/git/pull/2
[2]: https://www.quora.com/What-is-Google-Foobar-1
