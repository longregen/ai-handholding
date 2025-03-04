+++
title = "Keep Files Small"
date = "2025-03-04T10:17:02-05:00"
tags = []
+++

It has been long debated about at what size a code file is too big.  Some say
that it should be based on single responsibility principle (one class per
file), others say that large files can be situationally OK and it depends on
if it is causing problems.

Do not make files that are too large, if your RAG system for feeding code
context can only operate on a per-file level, you will blow out your context;
also, IDEs like Cursor will start failing to apply the patch created by the
LLM (and even when it succeeds, it can take quite a long time to apply the
patch anyway--for example, on Cursor 0.45.17, applying 55 edits on a 64KB file
takes).  At 128KB, you will have trouble getting Sonnet 3.7 to actually modify
the entire file (Sonnet's context window is only 200k tokens).

There is also little excuse for not keeping your files small; the LLM can
handle all the drudgery of getting the imports right on your split out file.

## Examples

- I asked Sonnet 3.7 in Cursor to move a small test class from a 471KB Python
  file to another file.  Although the individual edits were small, Sonnet 3.7
  did not propose well formed edits that Cursor's patcher was able to apply.
