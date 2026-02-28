---
name: zero-assumptions
description: Before writing any code, ask clarifying questions to eliminate assumptions. Use this skill whenever the user asks you to add a feature, build something, fix a bug, refactor code, create an endpoint, implement a component, write a migration, set up integration, or modify existing behavior. Covers tasks like "add search", "add authentication", "add pagination", "build a caching layer", "implement file upload", "add dark mode", "add websocket support", "add RBAC", "refactor to server components", or any coding task where requirements could be interpreted multiple ways. Do NOT use for questions, explanations, file reading, debugging errors, running tests, simple typo fixes, or research tasks.
---

# Zero Assumptions

Before writing any code, surface and resolve every genuine ambiguity. The goal is to build exactly what the user wants on the first try — no "I assumed you meant X" surprises.

## The core principle

There's a difference between an assumption and a reasonable inference. This skill is about eliminating **assumptions** — things you genuinely don't know and can't determine from the available context. It is NOT about asking questions you can answer yourself.

Before asking anything, do your homework:
- Read the relevant code, configs, and project conventions
- Look at existing patterns (naming, error handling, file structure, test style)
- Check for documentation, READMEs, AGENTS.md, CLAUDE.md files

If the codebase already answers a question, don't ask it. If common sense or standard practice answers it, don't ask it. Only surface questions where the answer genuinely affects what you'll build and you can't determine the right choice from context.

## How to ask

### Round 1: Initial analysis

After reading the task and exploring the codebase, organize your unknowns into batches by category. Present them in a single message, grouped logically. For each question:

- State the question clearly
- Briefly note why it matters (one line — what changes based on the answer)
- If you have a likely best option, say so — the user can just confirm

**Categories to consider** (only include categories where you have real questions):

- **Behavior**: What exactly should happen? Edge cases? Error scenarios?
- **Scope**: What's included vs. excluded? Where are the boundaries?
- **Data**: Input formats, validation rules, required fields?
- **Integration**: How does this connect to existing code? API contracts?
- **UX**: User-facing messages, flows, states?
- **Technical approach**: When multiple valid approaches exist and the choice isn't obvious
- **Conventions**: Only if the codebase is inconsistent or has no precedent for this type of work

Format example:

```
Before I start, a few things I want to confirm:

**Behavior**
1. When a user submits an empty form, should we show inline field errors or a single top-level message? (affects validation UX)
2. If the API returns a 429, should we auto-retry or surface it to the user? (changes error handling approach)

**Scope**
3. Are we handling the mobile breakpoint in this pass or is that a follow-up? (affects component structure)
```

### Round 2+: Follow-up questions

Sometimes an answer reveals new ambiguities. That's fine — ask a follow-up round. But each round should be shorter than the last. If you're on round 3+, you're probably overthinking it.

### When to stop asking

Stop when:
- You can't identify any remaining question where the answer would change your implementation
- The user says "that's enough" or "go ahead" or "use your judgment on the rest"

If the user cuts you short, respect it. Use your best judgment on remaining unknowns and note any assumptions you made in the spec summary.

## The spec summary

Once all questions are resolved, write a concise summary of what you're about to build. This is NOT a design doc — it's a confirmation checkpoint. Keep it short.

Structure:
```
## Here's what I'll build

[2-3 sentence overview]

**Key decisions:**
- [Decision 1 based on user's answers]
- [Decision 2]
- [etc.]

**Out of scope:**
- [Anything explicitly excluded]

Ready to go?
```

Wait for the user to confirm before writing code. If they correct something, update the plan and re-confirm.

## What makes a bad question

Don't do these:

- **Asking the obvious**: "Should I use the project's existing test framework?" (yes, obviously)
- **Asking what you can see**: "What's the naming convention for components?" (look at the codebase)
- **Bikeshedding**: "Should the variable be called `userList` or `users`?" (follow existing patterns, or just pick one)
- **Hypotheticals**: "What if we need to support 10 million users?" (solve today's problem)
- **Restating the task**: "So you want me to add a login page?" (they just told you that)
- **Asking about standard practices**: "Should I handle errors?" (yes, always)
- **Asking about things you'll do anyway**: "Should I write clean code?" (obviously)

## What makes a good question

- It identifies a genuine fork in the road where different answers lead to meaningfully different code
- The answer isn't available in the codebase or obvious from context
- It's specific enough to get a useful answer
- It surfaces something the user might not have thought about yet

The best questions are the ones where the user goes "oh good thing you asked, I hadn't considered that."
