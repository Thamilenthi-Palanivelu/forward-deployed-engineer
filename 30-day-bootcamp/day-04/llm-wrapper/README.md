# Reusable LLM API Wrapper

**Date:** *YYYY-MM-DD*

---

## Overview

*Describe the purpose of your LLM wrapper. What abstraction does it provide? Why is a wrapper useful for FDE work?*

*Your overview here*

---

## Supported Providers

- [ ] OpenAI (GPT-4, GPT-3.5)
- [ ] Anthropic (Claude)
- [ ] Google (Gemini)
- [ ] Open-source / local (Ollama, vLLM)
- [ ] *Additional provider*

---

## Installation

```bash
# Installation commands here
```

### Environment Variables

```bash
# Required API keys
export OPENAI_API_KEY="your-key-here"
export ANTHROPIC_API_KEY="your-key-here"
# Add others as needed
```

---

## Usage Examples

### Basic Completion

```python
# Show a basic usage example here
```

### Streaming Response

```python
# Show a streaming example here
```

### Switching Providers

```python
# Show how to switch between providers here
```

### With System Prompt

```python
# Show how to use a system prompt here
```

---

## Error Handling

*Describe how your wrapper handles common failure modes.*

| Error Scenario | How It Is Handled |
|---------------|-------------------|
| Rate limiting | *Your approach* |
| API key invalid | *Your approach* |
| Network timeout | *Your approach* |
| Token limit exceeded | *Your approach* |
| Provider unavailable | *Your approach* |

---

## Configuration

*Describe the configuration options available.*

| Parameter | Default | Description |
|-----------|---------|-------------|
| `provider` | *default* | *Which LLM provider to use* |
| `model` | *default* | *Which model to use* |
| `temperature` | *default* | *Sampling temperature* |
| `max_tokens` | *default* | *Maximum response length* |
| `timeout` | *default* | *Request timeout in seconds* |
| `retries` | *default* | *Number of retry attempts* |

---

## Architecture Notes

*Describe the design of your wrapper. What patterns did you use? How is it structured?*

*Your architecture notes here*

---

## What I Learned

*Reflect on building this wrapper. What was harder than expected? What would you do differently?*

- *Lesson 1*
- *Lesson 2*
- *Lesson 3*
