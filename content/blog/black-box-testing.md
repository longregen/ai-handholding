+++
title = "Black Box Testing"
date = "2025-03-03T21:18:37-05:00"
tags = []
+++

Black box testing says that you should test the functionality of a component
without knowing its internal structure.  By default, LLMs have difficulty
abiding with this, because by default the implementation file will be put into
the context, or the agent will have been tuned to pull up the implementation
to understand how to interface with it.  Sonnet 3.7 in Cursor also has a
strong tendency to try to make code consistent, which that it will try to
eliminate redundancies from the test files, even though black box testing
suggests it is better to keep the redundancy to avoid reflecting bugs from the
implementation directly in the test.

Ideally, it would be possible to mask out or summarize implementations when
loading files into the context, to avoid overfitting on internal
implementation details that should be hidden.  It would be necessary for the
architect to specify what the information hiding boundaries are.

## Examples

- I asked Sonnet 3.7 in Cursor to fix a failing test.  While it made the
  necessary fix, it also updated a hard-coded expected constant to instead be
  computed using the same algorithm as the original file, instead of
  preserving the constant as the test was originally written.  See also
  [Preparatory Refactoring]({{< relref "preparatory-refactoring.md" >}}).
