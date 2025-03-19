+++
title = "PTFM: Paste the documentation"
date = "2025-03-19T12:00:00-05:00"
tags = []
+++

One recurring challenge I find when using Sonnet grounded in the precise context of the problem I’m solving is its sudden invention of classes and methods in libraries that do not exist. A simple solution tends to be to copy and paste the docs, a tactic I call Prompt The Fine Manual, **PTFM**, the equivalent of telling humans to RTFM.

## The Idea Behind PTFM

The premise is straightforward: whenever I need the LLM to reference specifics—such as library functions, API endpoints, or configuration directives—I copy and paste the relevant pieces of documentation directly into my prompt. By doing so, I eliminate any ambiguity about the context or environment in which the code or configuration needs to run.

Rather than relying on the LLM’s sometimes fuzzy memory of a library’s API or a project’s historical usage, explicitly injecting the definitive source material into the conversation makes the LLM’s “thought process” more aligned with my current problem space, anchoring it in the actual job to be done.

## Why It Works

It's not hard to think that PTFM helps a lot. It takes a little more effort from the human operator, but it greatly improves the chances of an accurate solution.

LLMs are powerful, but they can drift when confronted with broad or ambiguous prompts. It is also well known that a large context tends to confuse it. Look for moments where it hallucinates some method in a well-known library that doesn't exist: that's when you should intervene and PTFM. I tend to give it a couple of chances (because I'm lazy to look up the particular page of documentation) before.

Having the reference in the context, in my opinion, makes it far easier for the model to generate code than to rely on its training data. The technique is especially helpful in cases where I’m dealing with obscure or recently updated libraries, frameworks, or configuration options.

## Example

I was configuring a Squid HTTP proxy for a research project, and struggling to make Claude understand how to draft appropriate Access Control Lists (ACLs) for filtering certain requests. The rules Sonnet 3.7 was coming up with simply did not exist, although maybe they were good ideas for issues and improvements to the Squid project.

I opened up Kagi, looked for "squid acl", and the first result was exactly what I wanted. I copied its content to the prompt for Claude and it immediately fixed the problem. Some of the example configurations from that page probably helped it to fix a few other errors: it deleted a lot of lines, more than I expected.
