---
layout: single
title: "A map reduce model of AI"
slug: a-map-reduce-model-of-ai
date: 2025-06-21
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

# Pull request level agents

# A map-reduce model
