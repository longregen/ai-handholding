+++
title = "The tail wagging the dog"
date = "2025-03-10T10:15:50-04:00"
tags = []
+++

The tail wagging the dog refers to a situation where small or unimportant
things are controlling the larger or more important things.  A common reason
this occurs in software engineering is when you get too absorbed in solving
some low level problem that you forgot the whole reason you were writing the
code in the first place.

LLMs are particularly susceptible to this problem.  The problem is that in the
most common chat modality, everything LLM does is put into the context.  While
the LLM has some capability of understanding what is more or less important,
if you put tons of irrelevant things in the context, it will become harder and
harder for it to remember what it should be doing.  Careful prompting at the
beginning can help, as is good context hygiene.  Claude Code does something
smart where it can ask a subagent to do a task in a dedicated context window
without polluting the global context.

## Examples

- If not carefully prompted, if you ask an LLM to think about how they would
  do something, they will often forget that they were only supposed to think
  about it and will go straight to trying to do the thing they were thinking
  about.
