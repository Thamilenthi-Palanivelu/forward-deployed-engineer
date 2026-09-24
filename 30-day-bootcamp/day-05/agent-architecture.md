# AI Agent Architecture

**Date:** *YYYY-MM-DD*

Design and document the architecture of an AI agent. Think through each component before you build.

---

## Agent Components Diagram

*Draw or paste an architecture diagram here. ASCII art, Mermaid syntax, or a link to an image all work.*

```
+-------------------+
|                   |
|   [Your diagram]  |
|                   |
+-------------------+
```

---

## Goal Definition

*What is this agent designed to accomplish? Be specific about the scope and boundaries.*

**Primary goal:** *your definition*

**In scope:** *what the agent should handle*

**Out of scope:** *what the agent should NOT handle*

---

## Reasoning Engine

*How does the agent decide what to do next? Describe the reasoning approach.*

- **LLM model used:** *model name and why*
- **Reasoning approach:** *e.g., ReAct, chain-of-thought, plan-then-execute*
- **Prompt structure:** *describe the system prompt and how the agent is instructed*
- **Decision-making process:** *how does it choose between available actions?*

---

## Memory System

*How does the agent maintain context and learn from past interactions?*

- **Short-term memory:** *e.g., conversation history, context window management*
- **Long-term memory:** *e.g., vector store, database, file system*
- **Memory retrieval:** *how does the agent access relevant memories?*
- **Memory limits:** *how do you handle context window limits?*

---

## Available Tools

*List every tool the agent can use and what it does.*

| Tool Name | Description | Input | Output |
|-----------|-------------|-------|--------|
| *Tool 1* | *what it does* | *expected input* | *expected output* |
| *Tool 2* | *what it does* | *expected input* | *expected output* |
| *Tool 3* | *what it does* | *expected input* | *expected output* |
| *Tool 4* | *what it does* | *expected input* | *expected output* |

---

## Feedback Loop

*How does the agent evaluate its own output and improve?*

- **Self-evaluation:** *how does it check if it succeeded?*
- **Error recovery:** *what happens when a tool call fails?*
- **Iteration limit:** *maximum number of reasoning steps before stopping*
- **Human-in-the-loop:** *when and how does it ask for human input?*

---

## Design Decisions

*Document the key design decisions and trade-offs you made.*

| Decision | Trade-off | Rationale |
|----------|-----------|-----------|
| *Decision 1* | *What you gave up* | *Why this was the right call* |
| *Decision 2* | *What you gave up* | *Why this was the right call* |
| *Decision 3* | *What you gave up* | *Why this was the right call* |

---

## Open Questions

*What are you still unsure about? What would you research or test further?*

1. *Question 1*
2. *Question 2*
3. *Question 3*
