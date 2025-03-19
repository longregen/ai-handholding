+++
title = "Rank Reasons"
date = "2025-03-19T11:00:00-05:00"
+++

One of the simplest and more effective strategies I've found to prompt LLMs efficiently is to ask them to generate and rank potential causes of some issue I'm having when coding.

Generally the conversation goes like this:

```
I'm having issues with «something». It seems like «this» or «that» is causing «thing» to do «something undesired». Can you come up with 7 plausible explanations why this would be the case? 
```

This approach has several benefits. First, it allows the AI to explore multiple possibilities without committing to a single explanation prematurely. Second, it helps surface potential issues that might not be immediately obvious, including edge cases or rare conditions. And third, I can now use all this output to guide the next steps. After the AI has described all the potential issues, I ask it to rank them from one to five, where one means "this is probably not the resolution" and five means "this is a blocker that is very likely to be causing the issue."

```
Now, rank these explanations of possible causes from 1 (actually not very relevant) to 5 (this is probably the #1 problem that is causing «something undesired»).
```

This ranking process forces the AI to evaluate the relative likelihood of each explanation and prioritize the most promising avenues for investigation. It's a way of applying a systematic approach to troubleshooting, even when the problem domain is complex or unfamiliar. I use "1" to "5" because I suspect that star rankings might be popular in the training data, and also to prevent the "1" in "10" from causing confusion at a token level. It's also important that the LLM exposes the reasoning first, before coming up with the ranking. You don't want random logit selection and the eagerness to be consistent to make the LLM justify a careless early judgement.