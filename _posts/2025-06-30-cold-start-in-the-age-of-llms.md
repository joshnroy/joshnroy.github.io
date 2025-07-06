---
layout: single
title: "Cold Start in the Age of LLMs"
slug: cold-start-in-the-age-of-llms
date: 2025-06-30
categories: blog
tags: [llm, ai, product-development]
excerpt: "Why Google's rules of machine learning don't apply to agents"
author_profile: true
---

*Originally published on [Bridger Substack](https://bridgergp.substack.com/p/evals) on Jun 30, 2025. This post was written as part of my employment at [Pillar Advisors](https://www.pillar-advisors.com/).* 

Google’s first rule of ML is: “Don’t be afraid to launch without machine learning.” That’s because traditional models needed large amounts of training data even to get started. This is the cold start problem: You need data to train a model, but don’t yet have a running model to collect feedback on.

Historically, engineers had two options:

1. Launch without ML: Use heuristics, collect user feedback, then layer in ML later.
2. Manually create a dataset: Time-intensive and often mismatched with future needs.

If you’re building an AI agent, launching without ML isn’t an option. Manual dataset curation can be extremely costly, and also brittle if your product direction changes.

## LLMs Don’t Require Training

This is an obvious statement, but fundamentally changes the ordering of early stage AI product development:

1. Prototype with prompts + context
2. Evaluate manually
3. De-risk product fit early
4. Only build eval sets once the product shape is clear

### Why It Matters

In the early stages of product development with LLMs, you’re trying to de-risk two axis:

1. Is the model “smart” enough to do what I want?
2. Is the surrounding product experience what I want?

With traditional ML development, answering these questions is extremely expensive. For example, let’s say we’re building an agent that does tax planning based on various scenarios. We first need to answer the question of whether models can reason through and perform the complex, multi-step calculations necessary (spoiler: they can’t yet). With an LLM, we can test this easily by uploading a redacted tax return to ChatGPT.

Additionally, prototyping with prompts and context first makes pivots in product direction much faster. Let’s say we wanted to change our agent to go from summarizing tax documents for accountants, to drafting an email to clients explaining their tax situation. Historically, this would require retraining a new model, with a new dataset of client-facing emails. With LLMs, it is a few lines of prompt changes.

## You Can’t Get Away from Evals

To go from early launch or prototype to production, you still do eventually need evals. Otherwise, you will quickly get to a point where you are unclear how to tune your prompts or context, without potentially breaking functionality.

However, the above ordering of development still helps: You can use data and feedback from your prototype to help build out your eval set.

## Takeaways

When building an AI application, we recommend the following ordering:

1. Design/Scope the application
2. Build an AI-Enabled prototype using a prompt-tuned LLM without codified evals
3. Collect user feedback on the product
4. Enter normal ML development cycle: collect dataset, run evals, iterate on model capabilities
5. Launch v1 product

*A guest post by Josh Roy*
