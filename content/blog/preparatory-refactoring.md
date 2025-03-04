+++
title = "Preparatory Refactoring"
date = "2025-03-03T21:24:52-05:00"
tags = []
+++

[Preparatory Refactoring](https://martinfowler.com/articles/preparatory-refactoring-example.html)
says that you should first refactor to make a change easy, and then make the
change.  The refactor change can be quite involved, but because it is
semantics preserving, it is easier to evaluate than the change itself.

Current LLMs, without a plan that says they should refactor first, don't
decompose changes in this way.  They will try to do everything at once.  They
also sometimes act a bit too much like that overenthusiastic junior engineer
who has taken the Boy Scout principle too seriously and keeps cleaning up
unrelated stuff while they're making a change.  Reviewing LLM changes is
important, and to make review easy, all of the refactors should happen ahead
of time as their own proposed changes.

Ideally, the LLM would be instructed to not do irrelevant refactors (NB:
anecdotally, Cursor Sonnet 3.7 is not great at instruction following, so this
doesn't work as well as you'd hope sometimes).  Alternately, a pre-pass on the
code the LLM expects to touch potentially should be done to give the LLM a
chance to do whatever refactoring it wants to do before it actually makes its
change.  Sometimes, context instructing the model to do good practices (like
making code have explicit type annotations) can make this problem worse, since
arguably the model was instructed to add annotations.  Accurately determining
the span of code the LLM should edit could also help.

## Examples

- I instructed an LLM to fix an import error from local changes I made in a
  file, but after fixing the imports it also added type annotations to some
  unannotated lambdas in the file.  Adding insult to injury, it did one of the
  annotations incorrectly, leading to an agent loop spiral.
