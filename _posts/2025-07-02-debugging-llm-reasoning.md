---
layout: single
title: "Debugging LLM Reasoning"
slug: debugging-llm-reasoning
date: 2025-07-02
categories: blog
tags: [llm, debugging, ai]
excerpt: "Adding reasoning fields to LLM outputs helps with debugging and trust"
author_profile: true
---

*Originally published on [Bridger Substack](https://bridgergp.substack.com/p/debugging-llm-reasoning) on Jul 2, 2025. This post was written as part of my employment at [Pillar Advisors](https://www.pillar-advisors.com/).* 

Machine learning systems are notoriously difficult to debug for a few reasons:

1. **Stochasticity**: Given non-repeatable results, you must run experiments consisting of multiple trials in order to determine the true behavior: the mean and variance of the results.
2. **Attribution**: When piping emails, documents, and bank transaction details into a machine learning system, it becomes very difficult to attribute importance to each factor.

The combination of both factors leads to a lack of interpretability: it is difficult to determine why an ML system acted the way it did. It could be missing inputs, trained incorrectly, or simply produce a random incorrect answer.

These same problems apply to LLM-based systems. LLMs may randomly answer incorrectly or hallucinate, and they integrate different input factors from prompts, tools, or input files.

Finding true solutions to stochasticity is still an open research problem, and fully attributing model behavior may not be feasible without strong constraints. However, solving interpretability well enough to be useful is quite simple.

## Having LLMs explain their reasoning

```json
{
  "result": "str"
  "reasoning": "str"
}
```

Adding a `reasoning` field to the structured output of any LLM call works surprisingly well. In practice it is often sufficient to read the model’s reasoning and identify any missing context or prompts that need to be updated.

### Example

> Which states did the client file taxes in?
>
> **Result**
>
> ```json
> {
>   "states": [
>     "NY",
>     "NJ"
>   ]
> }
> ```
>
> **Reasoning**
>
> The `<redacted>` attachment shows filings in both New York (IT-204) and New Jersey (NJ-1065) for the `<redacted>` tax year. While other financial statements indicate ongoing tax obligations in New York through `<redacted>`, these are listed as 'payables' and the `<redacted>` returns are the latest explicitly identified as filed tax returns.

This snippet comes from a real AI pipeline within Bridger. The reasoning field clearly shows why it thinks the client filed in NY and NJ.

## Building User Trust

In addition to debugging, model reasoning can be critical in building user trust. A model simply stating that the client filed in NY and NJ isn’t helpful, since it is unverifiable. The accountant must either blindly trust the model or redo the work.

Having the reasoning makes it much faster for a human to verify that the logic is correct. In this example, an accountant can look at the attachment, verify it is the right source of information, and quickly confirm the extracted states.
