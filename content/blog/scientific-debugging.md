+++
title = "Scientific Debugging"
date = "2025-03-09T22:18:30-04:00"
tags = []
+++

When there is a bug, there are broadly two ways you can try to fix it.  One
way is to randomly try things based on vibes and hope you get lucky.  The
other is to systematically examine your assumptions about how the system works
and figure out where reality mismatches your expectations.  I generally think
that the second approach of scientific debugging is better in the long run;
even if it takes you more time to do, you will walk away with a better
understanding of the codebase for next time.

A non-reasoning model is not going to do the scientific method.  It is going
to "guess" what the fix is, and try to one shot it.  If you are in an agent
loop, it can rerun the test suite to see if it worked or not, and then
randomly try things until it succeeds (but more likely, gets into a death
loop).

The general word on the street is you should use a reasoning model for
debugging (actually, people tend to prefer using models like Grok 3 or
DeepSeek-R1 for this sort of problem).  Personally, when I do AI coding, I am
still maintaining a pretty detailed mental model of how the code is supposed
to work, so I think it's pretty reasonable to also try to root cause it yourself (you don't have to fix it, if you tell the model what's wrong it will usually do the right thing).

## Examples

- One of the most horrifying death loops an agent LLM can get into is trying
  to fix misconfigurations in your environment; e.g., a package is missing for
  some reason.  One funny problem with Sonnet 3.7 is that it expects `pip` to
  be available, which it's not in the default venv created by `uv`, and it is
  incapable of figuring out what went wrong here, wasting a lot of tokens
  randomly flailing around.
