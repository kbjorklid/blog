---
title: 'Git Commit Workflow for Cline'
description: 'A simple Git Commit workflow for Cline'
date: 2025-05-29
tags: ['cline', 'ai-assisted coding']
---

[Cline](https://cline.bot) recently got a feature called '[Workflows](https://docs.cline.bot/features/slash-commands/workflows)'. I created a relatively simple
workflow for making AI write commit messages for me, and I think this serves like a simple but practical example on how to get started with workflows.

This is the workflow definition that Cline will feed to the GenAI Model:
````markdown
This describes the steps to create a new git commit out of the
uncommitted changes.

# Step 1

Run the following to get the diff of what is currently not committed to
git:
```bash
git --no-pager diff HEAD
```

# Step 2

Given what is not committed (as shown by the diff), and the task context,
formulate a title for a commit, and a commit message. If you know why the
change is made, include the reason in the commit message. Then execute
the following command (modify the value of the `-m` parameter suitably):
```bash
git add . && git commit -a -m "{title}

{description}"
```
````

To 'install' this workflow:
1. Copy the Markdown code form above
2. In cline, click the scales icon below the prompt text area.
3. Under 'Global workflows', in the 'New workflow file...' text box, write `commit.md` or something similar, and click the `+` button
4. Paste the code, and save.

To execute the workflow, type `/commit.md` to the execution prompt.

Generally, I would not advice the use of AI-generated commit messages as they tend to concentrate on the 'what' rather than the 'why'. That is, they tend to repeat what you could already deduce from reading the diff. However, for solo hobby projects where the alternative would be a worse message - or if you're going to amend the commit message manually - this is a good option.