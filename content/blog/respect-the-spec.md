+++
title = "Respect the Spec"
date = "2025-03-07T11:28:00-05:00"
tags = []
+++

When designing changes, it is important to keep in mind what parts of the
system you can change and what parts you cannot.  For example:

- If you expose a public API, you should prefer not to make a BC breaking
  change to the API, even if it would make your life easier if the API was
  different.

- If you interact with an external system, you have to conform to the API that
  actually exists, not some wishful thinking version that directly gives you
  what you want.

- If a test is failing, you should not delete it to make the test suite pass,
  you should understand if the test is right or not.

The common theme for all of these is that some parts of the system are part of the specification, and while *occasionally* the right thing to do is to change the spec, for day-to-day coding you would like to respect the spec.

LLMs are not very good at respecting the spec.  They'll happily delete tests,
change APIs, really do anything while they're coding.  Some of these
boundaries are common sense and could potentially be encoded in your prompt,
but some you will only discover when the LLM comes up with some new and
fascinating way to hack the reward function.  This is one of the most
important functions of reviewing LLM generated code; ensuring that it didn't
change the spec in an unaligned way.

## Examples

- Sonnet was failing to fix a test, so it replaced the contents of the test
  with `assert True`.

- I was trying to make a file well typed.  One public function was returning a
  dict with the key `pass`, and on a first pass Sonnet 3.7 tried to use the
  TypedDict class syntax, but this doesn't work because pass is reserved
  keyword.  To fix this, Sonnet decided to rename the key to `pass_`, which
  doesn't work for obvious reasons.
