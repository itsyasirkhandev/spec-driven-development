---
name: prompt-refiner
description: Refines basic, generic prompts into highly detailed, context-rich prompts. Use when the user asks to improve, enhance, or expand a prompt for another AI task.
---

# Prompt Refiner

## Goal

Enhance the current user prompt to make it super context-rich. Transform short, generic, context-free user requests into comprehensive, well-structured prompts ready to be fed into another AI coding agent. The generated prompt must include the full context 

## things to avoid

- dont anything like your a expert in this or that the prompt should be relavent to the codebase because the ai agent that we are using as a system prompt already setup and the ai agent know they are expert at coding. 
- don't include refined prompt or the final prompt or anything extra in the prompt content the prompt should be ready to copy paste so the user don't have to remove anything from the prompt.



## Process

### 1. **Analyze the Input Prompt**: Read the user's raw prompt and identify the core objective.
### 2. **MCP and Skills**: use and list the relavent MCP's and Skills make the prompt richer so add the section named 'skills and mcps' in the final prompt and list all the skills and mcp's the ai agent have to invoke

### 3. Interactive Interview Phase

Interview me relentlessly about every aspect of this plan until we reach a shared understanding. Walk down each branch of the design tree, resolving dependencies between decisions one-by-one. For each question, provide your recommended answer.

Ask the questions one at a time using the ask_question tool that will show the user ui so its easy for user to answer these questions, waiting for feedback on each question before continuing.

If a question can be answered by exploring the codebase, explore the codebase instead.

Sharpen fuzzy language
When the user uses vague or overloaded terms, propose a precise canonical term. "You're saying 'account' — do you mean the Customer or the User? Those are different things."

Discuss concrete scenarios
When domain relationships are being discussed, stress-test them with specific scenarios. Invent scenarios that probe edge cases and force the user to be precise about the boundaries between concepts.

Cross-reference with code
When the user states how something works, check whether the code agrees. If you find a contradiction, surface it: "Your code cancels entire Orders, but you just said partial cancellation is possible — which is right?"

## 4. details

- add the relevent code snippets and the offical docs fetched from the internet and add into the section named 'live data fetched from internet' and use the mcp tools and web fetch tool to fetch the offical docs/information if needed and for searching the docs/info related to our current codebase then first read the package.json and identify exact major,minor and patch version and then use the library major,minor and patch version to search and fetch the docs and attache the relevent info and code snippets. 
- include charts, tables, murmaid diagram if needed so the ai agent understand the prompt more comprehensivly.



## Output Format

Present your final output in markdown in an artifact named 'prompt_feature_name' the prompt should be well formated. 
