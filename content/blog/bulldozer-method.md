+++
title = "Bulldozer Method"
date = "2025-03-03T22:24:26-05:00"
tags = []
+++

The [Bulldozer Method](https://x.com/danluu/status/1570298241681616897) as
popularized by Dan Luu suggests that sometimes you can achieve results that
seem superhuman simply by just sitting down, doing the brute force work, and
then capitalizing on what you learn by doing this to get a velocity increase.
AI coding is the epitome of brute force work: you can just brute force large
refactoring problems if you are willing to spend enough tokens, or you can
have the LLM build the workflow you will use to brute force the problem.  Look
for opportunity in places where previously people had written off a problem as
"too much work".

## Examples

- A historical annoyance people have had with strongly typed languages like
  Haskell or Rust is when you make a change to some core function, and then
  you have to refactor half the universe to account for it (fearless
  refactoring, they say, because the type checker will help you fix it).  In
  many cases, the "read compile error, fix the problem" loop can be completely
  automated by an agentic LLM.

- I had some test cases with hard coded numbers that had wobbled and needed
  updating.  I simply asked the LLM to keep rerunning the test and updating
  the numbers as necessary.
