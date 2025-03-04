+++
title = "Stop Digging"
date = "2025-03-03T20:52:58-05:00"
tags = []
+++

Outside of very tactical situations, current models do not know how to stop
digging when they get into trouble.  Suppose that you want to implement
feature X.  You start working on it, but midway through you realize that it is
annoying and difficult to do because you should do Y first.  A human can know
to abort and go implement Y first; an LLM will *keep digging*, dutifully
trying to finish the original task it was assigned.  In some sense, this is
desirable, because you have a lot more control when the LLM does what is
asked, rather than what it *thinks* you actually want.

Usually, it is best to avoid getting into this situation in the first place.
For example, it's very popular to come up with a plan with a reasoning model
to feed to the coding model.  The planning phase can avoid asking the coding
model to do something that is ill advised without further preparation.
Second, agentic LLMs like Sonnet will proactively load files into its context,
read them, and do planning based on what it sees.  So the LLM might figure out
something that it needs to do without you having to tell it.

Ideally, a model would be able to realize that "something bad" has happened,
and ask the user for request.  Because this takes precious context, it may be
better for this detection to happen via a separate watchdog LLM instead.

# Examples

- After having made some changes that changed random numbers sampling on a
  Monte Carlo simulation, I asked Claude Code to fix all of the tests, some of
  which were snapshots on exact random sampling strategy.  However, it turns
  out that the new implementation was nondeterministic at test time, so the
  tests would nondeterministically pass/fail depending on sampling.  Claude
  Code was incapable of noticing that the tests were flipping between
  passing/failing, and after unsuccessfully trying to bash the tests into
  passing, started greatly relaxing the test conditions to account for
  nondeterminism, instead of proposing that we should refactor the simulation
  to sample deterministically.
