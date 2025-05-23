---
layout: single
title: "Front end & musings on the importance of UX in the age of Gen AI"
slug: front-end-ux-importance-gen-ai
date: 2025-05-08
categories: blog
tags: [ux, genai, front-end, software-engineering, javascript]
excerpt: "Before 2025, I have worked almost exclusively on back end, machine learning, and distributed systems projects and relatively little on front end, UI, or UX."
author_profile: true
---

Before 2025, I have worked almost exclusively on back end, machine learning, and distributed systems projects and relatively little on front end, UI, or UX. Since starting work as a founding engineer at a startup, I have been spending a lot more time thinking about what my user will actually interact with (spoilers: front-end and UX).

![Photo by Boitumelo on Unsplash](/assets/images/blog/coding-unsplash-photo.png)
*Photo by [Boitumelo](https://unsplash.com/@writecodenow?utm_source=medium&utm_medium=referral) on [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)*

> Front end is complicated, difficult, and under-appreciated

Websites are generally expected to work and be performant. When a website works, it's not particularly appreciated, but when it doesn't work, it is clearly negative. Given the optimizations that React and other libraries use, there are many complicated errors to debug, such as asynchronous refresh loops.

In today's GenAI climate, when tools like GitHub CoPilot and Cursor AI are helping write code, I think there's a feeling that front-end can be automated. In the extreme version, we can one-shot prompt an agent and it will build the entire front-end application. However, that still leaves us with one problem:

> The importance of front-end coding isn't in literally writing code, it's in writing the code that creates the right experience.

I entirely believe that we will be able to one-shot create common interfaces, ex: "Give me a tinder-style application that rates dog walkers", but evaluating whether your user actually desires that type of interface requires at minimum user empathy and at maximum A/B tests across users with different interfaces. Theoretically, these things might be optimizable, but seems unlikely to happen in the next 5–10 years.

As such, in my front-end journeys, I am focusing significantly less on standing out in the literal writing of code and much moreso on *which* code to write. Working on Full-Stack AI Companies (as defined by [Y Combinator](https://www.ycombinator.com/rfs)), it's quite unlikely that a user knows exactly the user flow that they want with all details. Even in a rather straightforward-seeming domain such as accounting (which I'm currently working on), there are many intricacies to create the optimal user experience.

Given the increasing abilities for GenAI to write code but the still-present gap between code requirements and user solutions, I have started thinking of myself a little bit less as a brick layer (code writer) and a little bit more as a designer. Of course, this has implications for the rest of our tech stack too — fundamentally, the user goals and experience dictate which data we need, which databases to use, and which targets that machine learning models need to predict. A fact that is easy to forget when in the jungles of backend, distributed, or machine learning code.