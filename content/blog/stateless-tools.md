+++
title = "Stateless Tools"
date = "2025-03-03T21:38:09-05:00"
tags = []
+++

Your tools should be stateless: every invocation is independent from every
other invocation, there should be no state that persists between each
invocation that has to be accounted for when doing the next invocation.
Unfortunately, shell is a very popular tool and it has a particulary
pernicious form of local state: current working directory.  Sonnet 3.7 is very
bad at keeping track of what the current working directory is.  Endeavor very
hard to setup the project so that all commands can be run from a single
directory.

Ideally, models would be tuned to prefer not to make tool commands that change
state, even if they are available.  If state is absolutely necessary,
continuously feeding the current state into the model could help improve
coherence.  The RP community probably has quite a lot of lessons here.

## Examples

- A TypeScript project was divided into three subcomponents: common, backend
  and frontend.  Each component was its own NPM module.  Cursor run from the
  root level of the project would have to cd into the appropriate component
  folder to run test commands, and would get confused about its current
  working directory.  It worked much better to instead open up a particular
  component as the workspace and work from there.
