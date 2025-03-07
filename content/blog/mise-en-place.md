+++
title = "Mise en Place"
date = "2025-03-06T22:25:53-05:00"
tags = []
+++

In cooking, *mise en place* refers to the practice of organizing and arranging
all of the ingredients that will be needed during a shift, so that one does
not have to scramble to find the things you need when you are on task.

Mise en Place for your LLM is ensuring that all of the rules, MCPs and general
development environment for your model may need are properly setup before you
have a task.  In my experience, Sonnet 3.7 is not very good at fixing a broken
environment; vibe coding to fix a mutable, live production environment is like
randomly copy pasting commands from StackOverflow and hoping that something
good will help.  More likely than not, you're going to just irreparably
destroy your environment.  So make sure that everything is setup correctly, so
that Sonnet doesn't go down a big rabbithole trying to debug why your
environment isn't working when as an agent it tries to run some tests.

## Examples

- Due to some `npm link` shenanigans, I had a broken VSCode environment where
  I wasn't picking up imports to another local project correctly.  When I
  asked Cursor to run lint and fix tests, it got fixated on trying to fix this
  brokenness (but was not able to work out that the fix it should do is run
  `npm unlink` in one of the project directories).
