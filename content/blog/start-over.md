+++
title = "Start Over"
date = "2025-03-19T10:00:00-05:00"
+++

When working with AI agents, it's often the case that we've veered off-track and we're having issues to get back to the main trail. The model might be building on incorrect assumptions or misunderstandings that occurred earlier in the chat.

Don't be afraid to start over from the beginning. The longer a conversation continues, the more these hallucinations can compound and reinforce each other. What begins as a small misunderstanding can snowball into completely unusable output.

Rather than trying to correct course mid-stream, it's often more efficient and cheaper to simply restart. Increasing the context window is known to reduce the quality of the output.

Cline and other agentic solutions have a mechanism to "restore" the conversation at a previous point. I like using this in combination with [Write Bullet Points](../write-bullet-points). I end up following this small recipe:

1. Describe the big change I want
2. Ask the LLM to create a list of bullet points to implement my big change, and write it in a file "TODO.txt"
3. Start implementing the changes
4. Go back to the moment in the conversation where the TODO.txt was just written
5. Tell the LLM that we already implemented some of those points, to read the current implementation, and pick up from here.

By starting over with the right context, I like to think that I'm optimizing for cost (no useless tokens in the input), performance (no long context causing the LLM to perform worse), and speed (longer contexts also make LLM responses slower).