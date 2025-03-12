+++
title = "Know Your Limits"
date = "2025-03-12T11:43:35-04:00"
tags = []
+++

It is important to know when you are out of your depth or you don't have the
tools available to do your job, so you can escalate and ask for help.

Sonnet 3.7 is not very good at knowing its limits.  If you want it to tell you
when it doesn't know how to do something, at minimum you will have to
explicitly prompt it (for example, Sonnet's system prompt instructs it to
explicitly warn a user about hallucinations if it is being asked about a very
niche topic.)  It is very important to only ask the LLM to do things that it
actually can do, especially when it's an agent.

## Examples

- Sonnet 3.7 deeply, deeply believes that it has the capability to make shell
  calls.  If you are doing agentic coding and there is no bash command
  available, if Sonnet decides that it needs to make a file executable, it
  will start creating random shell scripts on your filesystem to try in some
  weird proxy of the thing they actually wanted to do.  It's common for Sonnet
  to say, "I am going to do X" and then generate a tool call for Y, which is
  totally different.  The best thing to do in this situation is to improve the
  prompt (not perfect, Sonnet will forget) or just give Sonnet a tool that
  does the thing it wants to do (a specific tool that does one thing will
  prevent Sonnet from trying to do a generic bash call.)
