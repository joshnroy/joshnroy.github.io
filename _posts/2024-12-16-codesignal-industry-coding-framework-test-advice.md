---
layout: single
title: "Advice/Preparation for CodeSignal Industry Coding Framework Test & Reflections"
slug: codesignal-industry-coding-framework-test-advice
date: 2024-12-16
categories: blog
tags: [codesignal, software-engineering, interview-tips, interview, industry-coding-framework]
excerpt: "I recently took the CodeSignal Industry Coding Framework (ICF) test as part of a software engineering interview but found a notable lack of internet resources for preparation."
author_profile: true
---

I recently took the [CodeSignal Industry Coding Framework (ICF)](https://codesignal.com/resource/industry-coding-framework/) test as part of a software engineering interview but found a notable lack of internet resources for preparation (unlike for leetcode-style tests). This article aims to (1) offer advice on how to prepare and (2) provide general reflections on the test.

![Perfect Score (600/600) with 20m to spare](/assets/images/blog/codesignal-perfect-score.png)
*Perfect Score (600/600) with 20m to spare*

**Disclaimer: For the sake of the company and the integrity of the test, this will solely consist of advice and thoughts — not the questions themselves.**

## Preparation Advice

The ICF is designed to test several factors:
1. Coding speed (including debugging speed)
2. Adaptability under Changing Requirements
3. Code Design (Refactorability)

Coding speed itself is akin to taking the math section of a standardized test such as the GRE or SAT: a tester must quickly recognize the purpose of the test and implement a solution with minimal errors. In this case, something like a bug in the tester's code will cause *significant* slowdowns. A taker should code as quickly as possible without introducing errors. Fortunately or unfortunately, this speed comes from sheer practice with coding quickly. Something like [Leetcode](http://leetcode.com) will help with this, but I recommend trying to practice for ICF directly as described below.

The ICF Test itself is comprised of 4 levels, each of which gives the test taker some new requirement to implement. For specific details, the best resource is the [CodeSignal design document](https://web.archive.org/web/20230321142915/https://discover.codesignal.com/rs/659-AFH-023/images/Industry-Coding-Skills-Evaluation-Framework-CodeSignal-Skills-Evaluation-Lab-Short.pdf) itself. To ensure that code is easily refactorable, I recommend the following:

- Use Python if at all possible — Python's duck typing and support for easy refactoring (ex: Adding a new field to a dictionary) is invaluable
- Read Clean Code and other similar books — coding a short project with changing requirements is not fundamentally different from a long multi-year undertaking.
- Reduce [Cognitive Load](https://github.com/zakirullin/cognitive-load) — ex: Using names that are clear will make both initial implementation and refactoring significantly easier. ex 2: Using a for loop to implement a complicated list filtering operation instead of a list comprehension may be easier to maintain in the short span of time the test provides.
- Write the minimal amount of code required to accomplish the task while still maintaining extendability

The last point is one that I found particularly helpful. To expand, I will give a made-up example. At level 1, we need to implement an airplane control system where we must keep track of airplanes and their status (Scheduled, Flying, Complete) via `new_flight`, `start_flight`, and `end_flight` methods. A simple implementation is as follows:

```python
class FlightManager:
    def __init__(self):
        self.flights = dict()
    
    def new_flight(self, flight_id):
        if flight_id in self.flights:
            raise ValueError(f"Flight {flight_id} cannot be created since it already exists")
        self.flights[flight_id] = "Scheduled"
    
    def start_flight(self, flight_id):
        if flight_id not in self.flights:
            raise ValueError(f"Flight {flight_id} does not exist")
        self.flights[flight_id] = "Flying"
    
    def end_flight(self, flight_id):
        if flight_id not in self.flights:
            raise ValueError(f"Flight {flight_id} does not exist")
        self.flights[flight_id] = "Complete"
```

Though this may satisfy the requirements and be quick to implement, there is a major mistake with regards to extendability. If level 2 is to add an airplane-type (modifying `new_flight` and defining `get_airplane_type`) and level 3 is to add an estimated time to arrival, the current code design will be difficult. Given that we are taking a 4-part test where we will need to extend requirements, it is easier to assume that we will need to track more data and initialize the class at level 1 using dictionaries instead as follows. In general, Python dictionaries are almost always useful — you can store data in a key-value manner and filter keys/values as needed via list/set/dict comprehensions.

```python
class FlightManager:
    def __init__(self):
        self.flights = dict()
    
    def new_flight(self, flight_id):
        if flight_id in self.flights:
            raise ValueError(f"Flight {flight_id} cannot be created since it already exists")
        self.flights[flight_id] = {"status": "Scheduled"}
    
    def start_flight(self, flight_id):
        if flight_id not in self.flights:
            raise ValueError(f"Flight {flight_id} does not exist")
        self.flights[flight_id]["status"] = "Flying"
    
    def end_flight(self, flight_id):
        if flight_id not in self.flights:
            raise ValueError(f"Flight {flight_id} does not exist")
        self.flights[flight_id]["status"] = "Complete"
```

## How to Practice

[Leetcode](http://leetcode.com) is a go-to resource for algorithms and data structure questions, but I was unable to find an analogous resource with practice problems for the ICF. There are a few resources, but by far the most useful was GenAI.

- [The CodeSignal Document](https://web.archive.org/web/20240531125804/https://discover.codesignal.com/rs/659-AFH-023/images/Industry-Coding-Skills-Evaluation-Framework-CodeSignal-Skills-Evaluation-Lab-Short.pdf): Make sure you read this and know the time breakdown/general lines of code for each of the 4 sections of the test
- [Mock ICF](https://github.com/PaulLockett/CodeSignal_Practice_Industry_Coding_Framework): This GitHub codebase provides an implementation of the test — this is great to practice with but is only one test
- GenAI: Ask a chatbot (I used ChatGPT) to generate test questions

As with most hackable tests (relevant article [1](https://yanirseroussi.com/2023/05/26/how-hackable-are-automated-coding-assessments/), [2](https://paulgraham.com/lesson.html)), the key to doing well on the ICF is identifying key strategies (as discussed in the previous section) and practice. Though there are some practice tests online (ex: the mock ICF), I highly recommend placing the CodeSignal document into ChatGPT and asking it to give practice tests, one level at a time. Ask it to give code test cases in addition to the question so that you can verify your results by running tests. By completing these and ensuring that you stay within the time limits for each section, you can generate a nearly unlimited number of practice tests. I find that ChatGPT's tests were slightly too easy, but fairly accurate. See the last section on ChatGPT prompts for information on how to generate the test.

## Reflections and Thoughts

Unlike a Leetcode-style coding problem, the CodeSignal ICF is not about memorizing and using pattern recognition to retrieve the correct algorithm (ex: two-pointers). It is actually a fairly reasonable reflection of senior engineer-level work to have to adapt existing codebases to support new features. Overall, the driving goal behind ICF is much more similar to working than leetcode. However, there are two main issues I find: time limit and hackability. The time limit of a senior engineer's project is more likely to be on the scale of hours, days, or weeks rather than minutes. Additionally, as with [Goodhart's Law](https://en.wikipedia.org/wiki/Goodhart%27s_law), "when a measure becomes a target, it ceases to be a good measure". Given the somewhat-known nature of the test, it is possible to practice directly for it without necessarily becoming a better software engineer.

However, as I know from serving as an interviewer at [Two Sigma](http://twosigma.com) for 3 years, it is very difficult to quickly differentiate between any set of candidates based on a single test. CodeSignal's ICF is a step in the right direction as it it more similar to daily SWE work, and I hope that CodeSignal continues to iterate upon and reduce the test's hackability.

## ChatGPT Prompts

In this section, I include my prompts to generate the test, as reference for reproduction. I do not include the full output as it's fairly long and the input prompts should be all that's needed to reproduce.

![ChatGPT Prompt 1](/assets/images/blog/chatgpt-prompt-1.png)

![ChatGPT Prompt 2](/assets/images/blog/chatgpt-prompt-2.png)

![ChatGPT Prompt 3](/assets/images/blog/chatgpt-prompt-3.png)

![ChatGPT Prompt 4](/assets/images/blog/chatgpt-prompt-4.png)

![ChatGPT Prompt 5](/assets/images/blog/chatgpt-prompt-5.png)

![ChatGPT Prompt 6](/assets/images/blog/chatgpt-prompt-6.png)

![ChatGPT Prompt 7](/assets/images/blog/chatgpt-prompt-7.png)

![ChatGPT Prompt 8](/assets/images/blog/chatgpt-prompt-8.png)

![ChatGPT Prompt 9](/assets/images/blog/chatgpt-prompt-9.png)