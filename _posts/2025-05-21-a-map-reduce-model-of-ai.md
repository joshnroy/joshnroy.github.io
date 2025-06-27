---
layout: single
title: "A map reduce model of AI"
slug: a-map-reduce-model-of-ai
date: 2025-06-27
categories: blog
tags: [software-engineering, ai, machine-learning, llm]
excerpt: ""
author_profile: true
---

Both in work and in personal research, I have been thinking a lot about maximal efficiency gain using AI (or other forms of automation). Whether this is in fields like accounting (work), coding (work/side projects), or simply knowledge research (planning where to stay on a vacation), automation has a to offer in terms of speedup, but has a potential (human) bottleneck. In the rest of this article, I will discuss in terms of coding agents, as they are currently the most advanced of these areas.

# Prerequisite

In modern software development, I typically think at levels of abstraction: file-level, (git) commit level, pull request level, and project-level. Each of these has increasingly higher levels of responsibility and autonomy. Roughly speaking, you may trust an intern to do file -> commit level changes, a new grad to do commit -> pr level changes, a mid-level engineer to to pr -> project level, and a senior engineer to do project+. I'm omitting team-level, company-level, and industry-level changes here as they're too far away for today's current coding agents.

This closely mirrors the leveling system of Google and other similarly-tiered tech companies.

# File level agents

These have existed publicly for a while: Since ChatGPT was publicly released, professional programmers and hobbyists alike have been copying and pasting bits of code from the website. People have even been feeding in entire files and copying their replacements, but due to context window size, it was hard for LLMs to generate _too_ large a file or multiple files that work in conjunction.

# Git commit level agents

Next come file/commit level agents such as Cursor, Windsurf, and Github Copilot. These are not fully featured independent agents - in fact they're somewhere between file-level and commit-level, often requiring a human to approve changes or run integration tests (they often run unit tests independently).

# Pull request level agents

At the pull request level, we see agents such as Claude Code, Gemini CLI, Google Jules, and OpenAI Codex. The interface for these agents is not a code editing file (though they can show you one), but instead a chat interface where you iterate with the agents on a plan, steer their implementation, and ask them for revisions. This is a distinct step higher than the former category where you still look at the individual files at each edit-step. Instead you may ask these agents to make a pull request on your behalf and then request revisions.

# A map-reduce model

Given that agents are not yet at the point where I would put code into production without both a complete understanding and review, there is limited speedup that we can get from these agents. As of today's date, I still iterate with them to create a plan, have them asynchronously execute the plan, and then iterate on PR review. In such a case, the limitation of development speed is no longer my physical typing speed, but instead the speed of my ability to plan, understand, and review code. This is not unlike the work of a senior engineer with direct reports.

In such a world, we are limited to an approximate maximum of a 50% speedup. This in itself is quite large and may allow a startup with 2-3 engineers to work for much longer before hiring, but it still fundamentally limited. Without discussing the nature of unreviewed code here, I believe the only speedup possible is batch processing - aka a map-reduce model.

For example, if I have a backlog of tasks to do, I can process them in serial (scoping each one implementing each one, and testing each one independently). Or I can work in batch - first iterating on a plan for each one, then mapping their implementation to a series of coding agents, before finally doing a human-level map step consisting of reviewing the code and a reduce step of merging the code.
