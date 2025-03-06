+++
title = "Use MCP Servers"
date = "2025-03-06T11:18:04-05:00"
tags = []
+++

Model Context Protocol servers provide a standard interface for LLMs to
interact with their environment.  Cursor Agent mode and Claude Code use agents
extensively.  For example, instead of needing a separate RAG system (e.g., as
previously provided by Cursor) to find and feed the model relevant context
files, the LLM can instead spend tokens to go lookup what files it wants to
look at before deciding what to do.

The built-in MCP servers include very general functionality like "run a shell
command", which means that in principle they can do anything you might want.
However, what you will notice is that the models need to think up of the right
command every time an interaction occurs.  They're vibe coding every command,
which means that some nontrivial percentage of the time, they'll come up with
some weird command that isn't the one you want.  If there is a command that
you know should definitely be used, you can reduce cognitive load on the LLM
by having a dedicated MCP that standardizes what command to use.  Making a new
MCP server is easy because you can just ask the LLM to write it for you.

An alternative to MCP servers is to write detailed instructions in Cursor
rules about the correct command to use when using shell.  However, I find the
instruction following for these rules to be not very good, possibly because
Cursor is not reliably feeding this context to the model.

## Examples

- When I ask Sonnet 3.7 to test a change to a TypeScript file, it would come
  up with different variations of npm/vitest instead of consistently using the
  command that the project documentation instructed to be used.
