+++
title = "Code XOR Test"
date = "2025-03-19T13:00:00-05:00"
tags = []
+++

Suppose you’ve asked the agent to fix a failing test. The model might try to correct the code so that it complies with the test. Then, once it sees that its new code isn’t quite right, it goes back and “fixes” the test so that it passes. And this snowballs into a test of hundreds of lines that is testing a completely different thing that you expected it to, because at some point Claude decided that it needed to change the framework you are using.

Any stray hallucination in one side of the process gets smuggled and amplified in the other. Then the model dutifully compounds it further, especially as the context grows. Longer context windows generally cause confusion and worse performance.

So, just tell your agent:

> Please fix the code that is making the test fail. DO NOT touch the test files, only edit the implementation.

Or:

> Please fix this ill-written test, but don’t touch the code—just change the test file.

LLMs are generally pretty good at generating the code you wanted, but sometimes they’re brilliant at generating confusion—especially when they’re allowed to keep rewriting everything in sight. The best safeguard is to keep them on one side of the line.