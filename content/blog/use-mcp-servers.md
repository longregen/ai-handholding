+++
title = "Use MCP Servers"
date = "2025-03-06T11:18:04-05:00"
tags = []
+++

Model Context Protocol servers provide a standard interface for LLMs to
interact with their environment.  Cursor Agent mode and Claude Code use agents
extensively.  For example, instead of needing a separate RAG system (e.g., as
previously provided by Cursor) to find and feed the model relevant context
files, the LLM can instead call an MCP which will let it lookup what files it
wants to look at before deciding what to do.  Similarly, a model can run tests
or build and then immediately work on fixing problems when this occurs.  It is
clear that Anthropic's built-in MCP servers are useful, and you should use
agent mode when you can.

----

Epistemic status: this next section is theoretical, I have not attempted it in
practice yet.

A further question to ask is whether or not you should be writing your own MCP
servers.  One of the built-in MCP servers is a shell, so in practice you can
turn on YOLO mode in Cursor and add some instructions to your Cursor rules
about what commands to run and this actually works reasonably well.  But it's
really dangerous!  Arbitrary shell commands can do anything, and there are
plenty of shell commands in your LLMs pretraining set that will trash your
environment.  So you are mostly praying that your LLM doesn't go off the rails
some day (or you're a careful user and audit every command before running
them--let's be real, who's got time for that).

The alternative is to write an MCP server that exposes the commands that you
want your model to have access to (note, this is a bit different from what
most people are thinking of when they write MCPs to access various existing
platform APIs).  In principle, this should make it easier to control what
tools actually end up getting called, but as of March 2025 support for this in
Cursor is poor.  In particular, there is no direct way to have different MCP
servers on a per project basis, and the overall direction the ecosystem is
going with MCP servers are to provide tools that are universally applicable,
rather than the equivalent of `npm run` as an MCP server.

## Examples

- When I ask Sonnet 3.7 to typecheck a TypeScript project and fix errors, in
  agent mode it will use MCP to run the command, get the output, and decide
  what to do from there.  There is much more convenient than having to
  manually copy paste terminal output into the chat window.  It's important to
  prompt this appropriately (either in Cursor rules, or via an MCP), as the
  LLM is prone to hallucinating what command you should run.  For example, in
  my case, by default it hallucinates `npm run typecheck`, which on this
  project did not work.
