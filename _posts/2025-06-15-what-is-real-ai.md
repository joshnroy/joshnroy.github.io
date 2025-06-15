---
layout: single
title: "Opinion: What is real AI engineering?"
slug: what-is-real-ai-engineering
date: 2025-06-15
categories: blog
tags: [software-engineering, ai, machine-learning, llm]
excerpt: "I have been reading/seeing a lot of discussion around _real_ AI engineering"
author_profile: true
---

Recently, I have been reading/seeing a lot of discussion around _real_ AI engineering and wanted to weigh in.

# Preamble - why I am qualified to talk about this

I have been around the AI space to see multiple shifts: during my undergrad and master's degrees, I conducted [robotics/reinforcement learning research](https://scholar.google.com/citations?user=380VVtUAAAAJ&hl=en&oi=ao), was a teaching assistant for classes like computer vision and deep learning, and started my learning before the popularization of LLMs and even before the complete adoption of deep learning - my introductory natural language processing class was about non-deep bayesian and frequentist statistical methods.

During my industry experience, I have worked on large-scale reinforcement-learning based walking for robots at [NVIDIA](https://www.nvidia.com/), production-ready on-device computer vision trained using Reinforcement Learning from Human Feedback at [Cognex](https://www.cognex.com/), large-scale deployment of ML models across different environments at [Two Sigma](https://www.twosigma.com/), and LLM-based agentic AI at [Pillar Advisors](https://www.pillar-advisors.com/).

Throughout that time, I have seen phase shifts from [linear quadratic regulators](https://en.wikipedia.org/wiki/Linear%E2%80%93quadratic_regulator) to deep reinforcement learning controllers for robotic locamation, bag of words models for text-based autocomplete to deep and eventually large language models, and manual feature engineering + linear regression to non-linear/deep methods for stock trading.

From my vantage point - the current transition from train-it-yourself deep learning models to API/prompt based agentic systems is not all that different.

# What is AI anyway?

According to the [Wikipedia page](https://en.wikipedia.org/wiki/Artificial_intelligence), 

> Artificial intelligence (AI) is the capability of computational systems to perform tasks typically associated with human intelligence, such as learning, reasoning, problem-solving, perception, and decision-making.

This definition does not actually state anything about the method through which this computation is performed. It could be statistical pattern matching, [logical SAT solving](https://en.wikipedia.org/wiki/SAT_solver), or even rule-based systems.

# Perceived difficulty

One theory I have is that of perceived difficulty: "just calling an API" certainly seems a lot more difficult than writing your own transformer in PyTorch and training it yourself. This line of reasoning reminds me of two analogous ones from not long ago.

1. Deep Learning is not _real_ AI: for the reason that downloading a pre-trained ResNet and fine-tuning it on your set of image data is a lot easier than analysing your featureset, considering the logical interactions between different features, and creating your own feature set.
2. Using deep learning frameworks (ex: PyTorch, Tensorflow) is not really creating your own neural network: For the reason that stacking pre-written layers is a lot easier than writing backpropogation and auto-differentiation algorithms yourself.

It is important to make sure that you understand _why_ you are doing the things that you are doing/observing. For example: it is likely not important to manually compute the overlap of the supports of your training and test distributions, but it _is_ highly relevant to know when your data is non-overlapping and that no amount of hyperparameter tuning or training will solve the problem. To give a more immediately relevant example, it may not be important to know the specific entropy of your input data, but it is important to recognize that no amount of prompt engineering will overcome a 0 correlation between your input and output data.

On the note of difficulty: I strongly believe that we will never run out of complex, difficult, and interesting, problems to solve. The advancements of ResNet would be much more difficulty without PyTorch, large language models would not have been possible without automatic feature-learning and pre-training.

In today's day - there are problems such as creating complex multi-agentic reasoning systems, continual learning and updating of knowledge-bases, and ensuring graceful failure of AI, all of which would have been much more difficult without the API-level abstraction provided by modern hosted or locally run large language models.

# Conclusions

Of course, it is important to be and hire the type of AI Engineer that you desire: someone who can fine tune a neural network may not be the best suited at building agentic systems nor vice versa.

Whether or not the [scaling hypothesis](https://en.wikipedia.org/wiki/Neural_scaling_law) actually arrives at Artificial General Intelligence, they clearly has uses in rapid-prototyping and production systems and greatly simplify difficulty (ex: you no longer need a rigorous training set to even begin training a model). As such, I believe we should spend time focusing on the next, larger problems to solve, making the best use of tools at our disposal, which currently includes API-level abstraction over language models.
