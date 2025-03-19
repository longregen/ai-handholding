+++
title = "Cat With Names"
date = "2025-03-19T11:00:00-05:00"
+++

When working with large codebases, I often need to analyze multiple files at once to understand patterns, identify issues, or make consistent changes across the project. To make this process more efficient, I've developed a custom script I named "cat-with-names."

I use a simple script that takes some names of files. Usually I pipe files with `find` or `fd` into the script and the script wraps the content of each one of those files with the name and then I copy the output of that script so that I can paste that into Claude or ChatGPT or Deep Research and ask some particular question and recommendation and then I put that back into client.

The command typically looks something like this:
```
fd . -tfile '*.ts' | xargs cat-with-names | copy
```

This preserves the context of which file each piece of code comes from, making it easier for the LLM to understand the structure of the codebase. It also allows me to selectively include only the files that are relevant to my current task, rather than overwhelming the AI with the entire codebase.

The script itself is quite simple—it just prepends each file's content with its name in a clearly marked format. I suspect that these markers help preventing confusion; but this is just a hunch.

```
======
File: index.html

<!DOCTYPE html>
...
======
```

After getting recommendations or insights from other LLMs, I can then apply the suggested changes back to the original tool, usually Cline. This workflow is useful for all sorts of tasks, be it refactoring, bug hunting, or implementing new features.
