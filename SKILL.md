---
name: gauntlet-prompt
description: Turn an ordinary task prompt into a ready-to-run Gauntlet Loop prompt through focused clarification questions.
---

# Gauntlet Prompt

Help the user turn their rough task prompt into a complete, paste-ready Gauntlet Loop prompt. The result should guide an agent to build, inspect, critique, and iteratively improve a real deliverable against a concrete quality bar.

## Conversation flow

1. Start from the user's supplied prompt and any context already in the conversation. Do not make them repeat information they have given.
2. Identify only the missing details that materially affect the prompt. Typical gaps include:
   - the intended outcome, audience, and scope;
   - the quality bar, reference examples, or observable acceptance criteria;
   - what the agent can inspect or use (repository, files, tools, environment);
   - which aspects should be built or judged independently;
   - practical constraints such as platform, compatibility, time, budget, or dependencies;
   - a stopping rule that does not rely only on subjective claims like “perfect” or “amazing”.
3. Ask concise, easy-to-answer questions in conversational Spanish when the user is speaking Spanish; otherwise use their language. Group related gaps into one turn, prioritize the few that change the result, and offer sensible options when useful. Ask follow-up questions only where an answer still materially changes the final prompt. Do not ask every item in the list by default.
4. Where the user does not know a detail, propose a reasonable option based on the task and ask them to accept or correct it. For quality bars, suggest inspectable references or measurable checks; do not silently invent a benchmark or claim that a subjective bar is objective.
5. Once the essentials are known, produce the finished prompt. Avoid another confirmation round when the prompt is already complete.

## Writing the final prompt

- Make it self-contained and ready to paste into an agentic coding or creation environment.
- Preserve the user's goal, domain, preferences, constraints, and requested tools. Do not expand scope.
- State the desired outcome and concrete quality bar clearly. Prefer references, observable behavior, rendered output, acceptance criteria, or measurements the agent can actually inspect.
- Let the lead agent choose implementation details and decomposition unless the user specified them. Encourage parallel builders and independent critics only when the environment supports them and the task benefits from that structure.
- For each important workstream, have a builder produce or improve the deliverable and a separate critic inspect the actual result against the bar, identify the largest remaining gap, and send it back for another iteration.
- Define a practical stop condition: the acceptance criteria are met and the critic finds no material gap, a reasonable iteration or resource limit is reached, or the user stops the run. Never leave the agent in an unbounded loop.
- Include real verification steps appropriate to the task, and require the final response to summarize the deliverable, checks performed, remaining gaps, and any assumptions.
- Include progress reporting only if useful for a long-running task or requested by the user.
- Keep the prompt as concise as completeness allows. Do not include this skill's interview process in the generated prompt.

## Output

Return the generated prompt in a clearly delimited, copyable block. If a meaningful assumption remains, state it briefly outside the block. If the user asks for only a draft or a particular format, follow that request.
