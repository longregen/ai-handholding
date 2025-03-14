+++
title = "Rule of Three"
date = "2025-03-13T14:02:33-04:00"
tags = []
+++

The Rule of Three in software says that you should be willing to duplicate a
piece of code once, but on the third copy you should refactor.  This is a
refinement on DRY (Don't Repeat Yourself) accounting for the fact that it
might not necessarily be obvious how to eliminate a duplication, and waiting
until the third occurrence might clarify.  (See also [The Wrong
Abstraction](https://sandimetz.com/blog/2016/1/20/the-wrong-abstraction).)

LLMs love to duplicate code.  Think about how, absent any other prompting, if
you ask an LLM to modify a program, it will spit out a new copy of the program
with the changes requested.  For an LLM to decide to refactor code to remove
duplication requires a moment where the LLM proactively decides to go out of
their way to do some cleanup.  (Actually, Sonnet 3.7 also has some of this
inclination, but if you look at the Claude Code system prompt, they
specifically instruct the model to not be *too* proactive, since it's easy for
the model to lose track of what it's doing.)  To make matters worse, if code
is copy pasted everywhere in your codebase already, the LLM will assume that
you want it to continue copy pasting the code everywhere.  It's up to you to
ask the model to reduce duplication.

## Examples

- I asked the LLM to write tests for some functionality, and it ended up
  duplicating lots of logic between tests.  I had to explicitly ask it to
  factor helper methods when doing so.  (Another difficulty: when the LLM is
  writing a new test, it needs to know about the helper to use it.  In agent
  mode, you better hope it looks at the right file to find out about the
  helper!)
