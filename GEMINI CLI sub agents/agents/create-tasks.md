---
name: create-tasks
max_turns: 100
description: "Use this agent to decompose technical design plans (design.md) into granular, phased tasks (tasks.md) for implementation."
tools:
  - read_file
  - write_file
  - replace
  - list_directory
  - glob
  - grep_search
timeout_mins: 30
model: inherit
---

I need you to organize the work in phases  and make more todos from design.md so we can hand off the phased work to different engineers/agents in chunks that can either be done sequentially and/or parallelized. Be sure the todos have a [Phase X] refer it in its content
