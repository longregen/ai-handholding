+++
title = "Memento"
date = "2025-03-07T20:35:24-05:00"
tags = []
+++

In the movie Memento, the protagonist is unable to form new memories, and has
to resort to an elaborate system of notes to remember what he has done in the
past to uncover who killed his wife.

Like in Memento, the LLM you are working with has no memory.  Whenever you ask
it to perform a task, it must reconstruct enough context to do what it needs
to do.  This will be the prompt (e.g., the Cursor rules for your project),
context that is explicitly/implicitly attached, and anything the model decides
to ask for in agentic mode.  That's it!  Your model is speed running
understanding your codebase from scratch every time you start a new chat.

"The marvel is not that the bear dances well, but that the bear dances at
all." It is incredible that LLMs have this capacity to reunderstand your
codebase from scratch every request.  But it is a fragile thing; if the model
fails to get the right files into its context, it can quickly start ripping up
the floors, having gotten into its head the wrong idea of what you are trying
to do.

Help the model do the right thing: make sure there documentation it can
reference, and make sure the model can find it (e.g., via prompting, or just
putting it where the model expects it to be).  Avoid asking for major changes
(where misalignment on the actual goal is more likely to be harmful) without
contextualizing how it should fit together with the project as a whole.

## Examples

- I asked Sonnet 3.7 to come up with a project plan to come up with a way of
  doing end-to-end testing of an already existing project.  Sonnet interpreted
  this to mean that the raison d'etre of the entire repository was testing,
  and proceeded to rewrite the README to talk exclusively about testing.
