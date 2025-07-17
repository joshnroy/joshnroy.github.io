---
layout: single
title: "The Case for Embodied AI"
slug: the-case-for-embodied-ai
date: 2025-07-17
categories: blog
tags: [llm, debugging, ai, embodied-ai, robotics]
excerpt: "Even outside of robotics"
author_profile: true
---

Coming from a robotics background, the case for Embodied AI in robotics is pretty clear:
1. No matter how much analysis your AI can do, it has to take actions and drive a robot.
2. (Inverse) No Free Lunch: a representation is only useful in the case that it enables some downstream task. (Reverse of a representation that enables all tasks is better at none of them). I.E. Without training for action in mind, it is unlikely that a non-action-based representation will be sufficient for action.
3. 

# Montezuma's Revenge

During my undergrad and masters research, one of the largest (non-real-life) Embodied AI tasks was solving [Montezuma's Revenge]().

TODO: INSERT IMAGE of montezuma's revenge

Inspired by [Claude Plays Pokemon](), I came back to this game as a sort of LLM-test. I hypothesized that there were a few reasons that modern LLMs may do well (tested with OpenAI's 4o, Gemini 2.5 Pro, and Claude Sonnet 3.5. Not more advanced models due to lack of funding).

1. Montezuma's Revenge relies on general real-world context. For example, keys should be collected and open doors, skulls are bad, you should go up or down ladders, etc. Due to their large corpus of background and common-sense knowledge, LLMs should have this context.
2. Even though they aren't planning algorithms in the true sense of the word, LLMs are very good at putting together and acting on laid out plans (see chain of thought, TODO list tools, Claude Code)
3. With the addition of vision inputs, VLMs (Vision Language Models) should be able to make semantic sense of the world around them. This should be able to achieve the dream of playing games (and acting in the real world) based on pure visions (though as far as I am aware, Claude Plays Pokemon does not do this).

Starting with a mini-experiment - playing cartpole - I initially found quite negative results, and the LLMs were unable to even identify the angle of the cart properly and performed approximately at random chance. After some prompt tuning to get the visual image understanding correct, it did much better, regularly achieving 100+ reward per episode. 

I then moved to Montezuma's Revenge.

TODO: INSERT IMAGE OF THE FIRST LEVEL

I was initially quite hopeful, with the agent picking actions like `down` and climbing down the initial ladder, with reasoning such as `I must reach the bottom` or `I must reach the key`. However, as the floor right under the ladder is an escalator (it pushes the character to the side), the agent initially fell off the platform to its death.

I tried a few methods to get around this, such as explaining what and how to identify escalators, explaining fall damage, and even giving hardcoded instructions to the agent telling it to jump to the platform on the left. But I was unable to get it to progress further.

I suspect with even more prompting (or perhaps even a RAG-system with relevant video game or Montezuma's Revenge experiences/actions), it may be possible to get around this. But I had significantly hoped that it would not require so much architecture - that the VLM itself had enough experience via pre-training and enough ability to adapt based on test-time reasoning. This likely indicates (at least) one of three things:

1. The model itself does not have enough visual or language based experience with video games
2. The model's sense of intuitive physics or other embodied qualities is incomplete.
3. The visual perception system is not yet sufficient to do high-level reasoning.


# Computer Use Agent (Tax-Specific Software)

# Conclusions and Future Steps
