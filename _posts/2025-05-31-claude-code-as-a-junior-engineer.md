---
layout: single
title: "Claude Code as a junior engineer and thoughts on the future of software engineering"
slug: clauude-code-as-a-junior-engineer
date: 2025-05-31
categories: blog
tags: [software-engineering, claude, ai, llm, code-automation]
excerpt: ""
author_profile: true
---

The past couple weeks, I finally switched from [GitHub Copilot](https://github.com/features/copilot) to [Claude Code](https://docs.anthropic.com/en/docs/claude-code/overview) following a week-long exercise I did, writing the front-end NextJS/react code for my employer's front end without an code assistance (think writing in VIM with only non-language specific completions).

After the first week, I decided that I'm actually quite good at reasoning through and writing code myself and that getting llm-completed snippets was minorly helpful but not a huge difference from my usual workflow inside a tool such as [VS Code](https://code.visualstudio.com/). Moreover, the real code automation was going to come from higher level thinking (ex: architecture, product thinking, UI/UX design) rather than thinking about the code and manually approving each bit.

Quite similar to hiring a junior engineer, I want to utilize one of these agents to delete/delegate a task of mine, not allow it to happen slightly faster. It seems that major players in the space thought the saem way, with the recent announcements of [Google's Jules](https://blog.google/technology/google-labs/jules/), [OpenAI Codex](https://openai.com/index/introducing-codex/), and [Claude Code GitHub Actions](https://docs.anthropic.com/en/docs/claude-code/github-actions). Of course, I missed the opportunity to write about this idea of mine, so you'll have to take my word that I thought of it before these were widely announced.

When working on a new user flow in our internal application, I first had to make a mockup/wireframe to get customer/CTO buy in. Rather than making one in popular tools like Figma or draw.io, I decided to have Claude Code come up with a minimally functional prototype embedded within our codebase, with the following restrictions;

1. It can import react components from elsewhere in our front-end codebase
2. It should be entirely separate - nothing should depend on it
3. It should be easy to modify for a human
4. The code should not interact with our back-end codebase, it should make up any data that was needed.

For the first time in my career, I watched the code Claude generated fly by in my terminal, but didn't worry too much about structure. Though I did instruct it to break things into logical components (ex: Make the overall layout of the page separate from the email threads component, separate from the email component). Much to my surprise, I had a mostly-functional prototype within an hour and entirely demoaable prototype within 2 hours, including some fairly complex behavior such as state transitions for emails (think archiving/unarching emails, replying to emails). Without going into too much detail, our product was a variant on a combination of a task list and an email client.

After surprising my team with the demo-implementation speed, I got feedback and began working on the production version. Much to my surprise, Claude (Sunnet 3.7 for the demo, but Opus 4/Sonnet 4 for the prod code) made sane decisions about issues like [Prop Drilling](https://www.geeksforgeeks.org/what-is-prop-drilling-and-how-to-avoid-it/). Over the past couple weeks, I've come to the following workflow that seems to work the best with Claude Code:

0. Open Claude Code in the directory that contains both my front-end and back-end repos. This allowed Claude to cross-reference as a human would, or even make sequential updates to both.
1. Tell Claude to write any plans to a specific file (not `CLAUDE.md`, but it could be) and re-read from that file after re-starts or compacting chat what-is-prop-drilling-and-how-to-avoid-it
2. Tell Claude to document industry best practices, codebase best-practices, and personal preferences within `CLAUDE.md`. I told it to add things there whenever I changed something.
3. When implementing a feature, start by telling it to read the relevant files of the codebase and propose a plan (this is similar to a design doc). Just within the past couple days, I discovered the [ultrathink capabilities](https://www.anthropic.com/engineering/claude-code-best-practices), so will have to play with those in the next few days.
4. Iterate on the design doc until I am happy with it. This reminded me quite a bit of the process of working with an intern or a new junior engineer; they are intelligent but may not have the experience to know the specific best practices for tools or layouts of codebases. For example, I frequently would tell Claude that the component it wants already exists.
5. Once I'm happy on the design, I would tell Claude to implement. Initially, I would monitor each code change and give feedback immediately, but this was quite slow. After a bit of feedback (and telling it to update `CLAUDE.md`), it seemed to better understand what I want.
6. Eventually, I allowed it to modify files, use all read-commands, and run builds/tests. This way, it would be fairly certain that the code worked before I did the user testing. Rather than trying to give code feedback at the pre-commit stage, once it had working code, I would ask it to create a PR and then give feedback as I would to another engineer.
7. Rather than commenting directly in the PR, I would tell the feedback to Claude directly as a bulleted list. 

This process ended up being quite quick for cases where I already knew the software architecture that I desired or was able to determine it by step 4. If I had (or wanted) to change the design after the main implementation, getting Claude to actually undo and redo things was somewhat difficult - it would stick to the existing codebase or preferences that I had previously expressed.

Using Google's Leveling System, this places Claude solidly at a L3 - it can independently implement well-defined and scoped features with some feedback (at the PR stage), definitely a step up from in-IDE agents!

I'm excited to play with the aforementioned coding agents that operate more explicitly at the PR level, I am somewhat concerned about the back-and forth design that is required (stage 1-3) so that we can give it proper context to do it's job.

Looking to the future, I believe there will be a day where the code itself will be entirely auto-generated. In the past couple weeks, approximately 50-70% of the code I'm writing is written through Claude code (with major guidance/oversight/multiple rounds of code reviews), but I am looking forward for the future where humans can spend less effort on the bricklaying of writing code and more on the design and purpose. Just as automatic garbage collection and code optimization in compilers allowed engineers to focus on higher order programming, I believe this wave of AI will not replace our jobs but allow us to operate at higher levels and make more impact with the same effort.
