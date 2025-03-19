+++
title = "Ask Multiple Experts"
date = "2025-03-19T11:00:00-05:00"
+++

Sometimes progress stalls, and we don't know how to continue. The conversation with the LLM or Agent seems to be going in circles, or the solutions proposed aren't quite hitting the mark. A useful technique in these situations is to assemble a council of multiple AI experts. 

When I think progress has really stalled and neither myself or the LLM will be able to figure out how to fix it, I follow this recipe:

1. Ask the LLM to describe everything that we've done so far: Create a summary of the problem, the approaches we've tried, and the current state of the solution.
2. I copy and paste that summary into multiple AI systems: o1 with Deep Research, a clean Claude, a DeepSeek instance, Kagi, Perplexity...
3. Copy and paste the solutions into the main agent, following this template:

```
We were working on the following problem definition:
${summary (output of point 1)}

Here is what multiple experts have proposed as a solution:
====
Expert 1, Alex:
${solution 1}
====
Expert 2, Beatrice:
${solution 2}
====
Expert 3, Carl:
${solution 3}
====
Expert 4, Daniel:
${solution 4}
====

Based on all these proposals, think about what you think would be the best solution and implement it.
```

Each model has its own training data, architecture, biases and "way of thinking" about problems. This recipe tries to extract the best out of those biases and differences.

It is particularly effective for complex problems where specialized knowledge is required. It helps break through the issue and opens up new avenues of exploration that Sonnet might not have discovered on its own.

