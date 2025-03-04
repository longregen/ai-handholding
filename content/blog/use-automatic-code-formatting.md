+++
title = "Use Automatic Code Formatting"
date = "2025-03-04T09:57:41-05:00"
tags = []
+++

Automatic code formatting tools like gofmt, rustfmt and black help enforce a
consistent coding style across your codebase.  LLMs are generally not very
good at following mechanical rules like "lines with no content on them should
have no trailing spaces even if the indentation level is non-zero" or "make
sure a line is wrapped at 78 columns."  Use the right tool for the job.

This applies to lint fixes too: prefer lints that can be automatically fixed,
and don't waste LLM capacity having the LLM fix them; save it for the hard stuff.
