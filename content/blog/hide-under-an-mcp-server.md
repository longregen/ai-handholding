+++
title = "Hide Under an MCP Server"
date = "2025-03-19T11:00:00-05:00"
+++

When working with AI agents on complex systems, we often encounter processes that generate overwhelming amounts of output. Build logs, test results, and system messages can quickly consume the limited context window of an LLM, leaving little room for actual problem-solving.

For example, when using Nix, the build process outputs extensive information. When tests fail, particularly those involving virtual machines, the output includes all the dmesg logs and system messages. This verbose output can overwhelm the AI agent and make it difficult to focus on the actual issue.

A solution I found to this problem was to hide these complex operations behind an MCP (Model Context Protocol) server. Instead of feeding all the raw output directly to the LLM, the MCP server processes this information and returns only a concise summary of the relevant details. I use Haiku to summarize the output.

When a Nix test fails, rather than showing all the output, the MCP server can extract just the critical error information and present it to the agent. This approach preserves valuable context window space and helps the agent focus on solving the actual problem rather than getting lost in implementation details.

By filtering out the noise and highlighting the signal, MCP servers enable more efficient problem-solving and reduce the risk of the agent becoming overwhelmed or distracted by irrelevant information. This is particularly valuable when working with complex systems where the volume of output can be substantial.
