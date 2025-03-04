+++
title = "Requirements, not Solutions"
date = "2025-03-03T22:45:39-05:00"
tags = []
+++

In human software engineering, a common antipattern when trying to figure out
what to do is to jump straight to proposing solutions, without forcing
everyone to clearly articulate what all the requirements are.  Often, your
problem space is constrained enough that once you write down all of the
requirements, the solution is uniquely determined; without the requirements,
it's easy to devolve into a haze of arguing over particular solutions.

The LLM knows nothing about your requirements.  When you ask it to do
something without specifying all of the constraints, it will fill in all the
blanks with the most probable answers from the universe of its training set.
Maybe this is fine. But if you need something more custom, it's up to you to
actually tell the LLM about it.  If you ask the LLM something too
underspecified and it misunderstands you, it's best to edit the original
prompt and try again; because previous conversation stays in the context,
leaving the incorrect interpretation in the context will make it harder for
the LLM to get to the correct part of the latent space that lines up with your
requirements.

By the way, if you are *certain* some aspects of the solution should work a
particular way, it's very helpful to tell the LLM about it, because that will
also help you get to the right latent space.  And it's also important to
be *right* about this, because the LLM will try very hard to follow what
you ask it to do, even if it's inappropriate.

## Examples

- If you ask Sonnet to make a visualization, chances are it will generate you
  an SVG.  But if you specify that it needs to be interactive, it will give
  you a React application instead.  Huge divergence based on one key word!
