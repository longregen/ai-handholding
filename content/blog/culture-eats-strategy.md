+++
title = "Culture Eats Strategy"
date = "2025-03-12T22:56:14-04:00"
tags = []
+++

Culture Eats Strategy (For Breakfast) says no matter how good your strategy
is, the culture of your team isn't capable of executing it.  If your problem
is execution, look to change the culture instead of trying to come up with
increasingly elaborate strategies.

By default, your LLM lives in a certain part of the "latent space":  when you
ask it to generate code, it will generate it with a style that is based off of
how it was fine tuned, as well as its context window up until the point (this
includes the system prompt as well as any files it's read into the context.)
This style is self-reinforcing: if a lot of the text in the context window
that uses a library, the LLM will continue to use that library--conversely, if
the library is not mentioned at all and the LLM is not fine-tuned to reach for
it by default, it will not use it (there are exceptions, but this is a reasonably
good description of how Sonnet 3.7 will behave.)

If the LLM is consistently doing things you don't like, you need to change its
culture: you need to put it in a different part of the latent space.  This
could be adding a rule to your Cursor rules (modifying the prompt), but it can
also be refactoring existing code to follow the style you want the LLM to
follow, since LLMs are trained to predict the next token in context.  The
fine-tune, the prompt and the codebase are the culture.  One you can't change,
and the codebase is a lot bigger than the prompt and ultimately will have a
dominating effect.

## Examples

- Sonnet 3.7's house style is to prefer synchronous over asynchronous Python.
  To get it to reliably write new code using async, it was necessary to force
  it to port most of the existing code in my codebase to be async.
