+++
title = "Read the Docs"
date = "2025-03-04T23:11:23-05:00"
tags = []
+++

When you're learning to use a new framework or library, simple uses
of the software can be done just by copy pasting code from tutorials
and tweaking them as necessary.  But at some point, it's a good idea to just
slog through reading the docs from top-to-bottom, to get a full understanding of what is and is not possible in the software.

One of the big wins of AI coding is that LLMs know so many things from their
pretraining.  For extremely popular frameworks that occur prominently in the
pretraining set, an LLM is likely to have memorized most aspects of how to use
the framework.  But for things that are not so common or beyond the knowledge
cutoff, you will likely get a model that hallucinates things.  Ideally, an
agentic model would know to do a web search and find the docs it needs.
However, Sonnet does not currently support web search, so you have to manually
feed it documentation pages as needed.  Fortunately, Cursor makes this very
convenient: simply dropping a URL inside a chat message will include its
contents for the LLM.

## Examples

- I was trying to use the LLM to write some YAML that configured to call a
  Python function to do some evaluation.  Initially, the model hallucinated
  how this hookup should work.  After providing the manual as context the
  model understood how to fix the error and also updated the output format of
  its function to match the documentation guidance.
