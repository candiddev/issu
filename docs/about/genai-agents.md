---
categories:
- feature
description: Issu helps GenAI agents perform work within your code repositories.
title: GenAI Agents
type: docs
---

LLMs love raw markdown, and Issu's markdown and frontmatter format make it trivial to assign work, set goals, and boost your productivity:

**Prompt:**\
Read the contents of issues/185.md and propose a solution for resolving it within the web/src code

**LLM:**\
To resolve issue #185 within the web/src code, I'll follow these steps:

1. __Understand the Issue__: Read the contents of `issues/185.md` to understand the problem description.
2. __Identify Relevant Code Files__: Search for any mentions of the issue in the web/src directory.
3. __Analyze Code Changes__: Make targeted changes to resolve the issue in the identified files using replace_in_file.
4. __Test Changes__: Use browser_action to launch the web application and verify that the issue is resolved.

Would you like me to proceed with these steps?

**Input:**\
yes

**LLM:**\
To proceed with the solution for issue #185, I'll focus on the following steps:

1. __Create a Dataset Library__: Implement the `Dataset` class and related functions as described in the notes.
2. __Refactor State Management__: Update the existing state management to use the new `Dataset` library.
3. __Test Changes__: Use browser_action to launch the web application and verify that the changes are working as expected.

Would you like me to start with step 1, creating the Dataset library?
