---
name: design
description: use this skill when user ask to create the create the technical design document/plan (design.md).
---

> **Quality bar**: Before writing a single line, read [EXAMPLE.md](EXAMPLE.md). Every `design.md` you produce must match the format, structure, and level of detail shown in `EXAMPLE.md` exactly. This is non-negotiable. If you cannot meet this standard, and you must use all the skills and mcp's and tools difined in the spec.md of section 8 'Relevant MCPs, Skills, and Tools'  when creating the technical design plan (design.md) don't miss that its important.


## Workflow

### 1. Locate the Spec

Use `list_dir` or `grep_search` to find the target folder in `/specs/`
(e.g., `/specs/001-feature-name/spec.md`). Read the `spec.md` in full.

### 2. Interactive Interview Phase ( if there is a need for it )

Interview me relentlessly about every aspect of this plan until we reach a shared understanding. Walk down each branch of the design tree, resolving dependencies between decisions one-by-one. For each question, provide your recommended answer.

Ask the questions one at a time using the ask_question tool that will show me ui so its easy for me to answer these questions, waiting for feedback on each question before continuing.

If a question can be answered by exploring the codebase, explore the codebase instead.

Sharpen fuzzy language
When the user uses vague or overloaded terms, propose a precise canonical term. "You're saying 'account' — do you mean the Customer or the User? Those are different things."

Discuss concrete scenarios
When domain relationships are being discussed, stress-test them with specific scenarios. Invent scenarios that probe edge cases and force the user to be precise about the boundaries between concepts.

Cross-reference with code
When the user states how something works, check whether the code agrees. If you find a contradiction, surface it: "Your code cancels entire Orders, but you just said partial cancellation is possible — which is right?"


### 3. Generate design.md

- **CRITICAL STEP**: You must use the `view_file` tool to read and understand the `EXAMPLE.md` file before creating the technical design. The `EXAMPLE.md` file includes all the detailed instructions and full examples of the chat sidebar and exactly how to create the technical design (`design.md`) file.
- Create `design.md` inside the **same folder** as the `spec.md`.



