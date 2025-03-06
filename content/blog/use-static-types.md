+++
title = "Use Static Types"
date = "2025-03-06T10:42:57-05:00"
tags = []
+++

The eternal debate between dynamic and static type systems concerns the
tradeoff between ease of prototyping and long term maintainability.  The rise
of LLMs greatly reduces the pressure to choose a language that is good at
prototyping, since the LLM can cover up for boilerplate and refactors.  Choose
accordingly.  You will want an agent setup where the LLM is informed about
type errors after changes they make, so they can easily tell what other files
they need to update when doing refactors.  Be careful about your token costs.

Unfortunately, the training corpus highly emphasizes Python and JavaScript.
Their typed offerings are workable, but as both are gradual type systems you
will need to carefully setup the typechecker settings to be strict (or
carefully prompt your LLM to setup the settings properly).

In principle, Rust should be a good target language for LLMs.  However, LLMs
are not as good at generating Rust as they are for Python/JavaScript.
