# AI Design Pattern Cheatsheet

## Pattern Reference

| Pattern Name | One-Sentence Summary | When to Use | When NOT to Use |
|-------------|---------------------|-------------|-----------------|
| **RAG (Retrieval-Augmented Generation)** | Augment LLM responses with retrieved context from a knowledge base to provide grounded, up-to-date answers. | When you need answers grounded in specific documents, proprietary data, or information that changes frequently. | When the LLM's built-in knowledge is sufficient, or when source documents are unstructured noise with no clear retrieval signal. |
| **Fine-Tuning** | Adapt a pre-trained model's weights on domain-specific data to improve performance on a narrow task. | When you have consistent formatting/style needs, domain-specific terminology, or a well-defined task with labeled training data (hundreds to thousands of examples). | When you can achieve results with prompt engineering or RAG; when you lack sufficient quality training data; when the task requires up-to-date knowledge (fine-tuning bakes in a point-in-time snapshot). |
| **Chatbot / Conversational Agent** | A multi-turn conversational interface that maintains context across exchanges to assist users interactively. | When the interaction is naturally conversational, users need follow-up capability, or the task benefits from clarifying questions. | When users need a single, definitive answer (use search or a structured form instead); when conversation history management is too costly or complex for the value delivered. |
| **Knowledge Agent** | An autonomous agent that plans, uses tools (search, APIs, code execution), and reasons step-by-step to answer complex questions. | When questions require multi-step reasoning, combining multiple data sources, or dynamic tool use that cannot be predetermined. | When queries are simple lookups (use RAG instead); when latency and cost are tightly constrained (agents make multiple LLM calls); when deterministic behavior is required. |
| **Contact Center AI** | AI-powered customer support that handles inquiries, routes to humans when needed, and assists live agents with suggestions. | When you have high-volume, repetitive support queries with clear resolution paths; when you want to augment human agents rather than replace them. | When customer interactions require high empathy or complex judgment; when incorrect answers carry significant legal/financial risk without human review. |
| **Recommendation Engine** | Use AI to suggest relevant items, content, or actions based on user behavior, preferences, and context. | When you have sufficient user interaction data, a catalog of items to recommend, and the recommendations meaningfully improve user experience. | When you have too little user data for personalization (cold start); when recommendations could create filter bubbles with negative consequences; when a simple rule-based approach would suffice. |
| **Autonomous Workflow** | An AI system that executes multi-step business processes end-to-end with minimal human intervention. | When you have well-defined, repeatable workflows with clear success criteria; when the cost of human execution is high and error tolerance allows for AI-driven decisions. | When the workflow involves high-stakes decisions requiring human judgment; when the process is too variable or ambiguous for reliable automation; when regulatory requirements mandate human oversight. |

## Quick Decision Framework

*Use this flowchart to select the right pattern:*

```
Start: What is the core need?
│
├─ "Answer questions from our documents"
│   └─ → RAG
│
├─ "Have a conversation with users"
│   ├─ Simple Q&A → Chatbot
│   └─ Complex, multi-step reasoning → Knowledge Agent
│
├─ "Handle customer support"
│   └─ → Contact Center AI
│
├─ "Recommend things to users"
│   └─ → Recommendation Engine
│
├─ "Automate a business process"
│   └─ → Autonomous Workflow
│
└─ "Adapt model behavior to our domain"
    ├─ Have 500+ labeled examples → Fine-Tuning
    └─ Fewer examples → Prompt Engineering + RAG
```

## Pattern Combination Matrix

*Some patterns work well together. Check this matrix for common pairings.*

| Combination | Use Case | Example |
|-------------|----------|---------|
| RAG + Chatbot | *Conversational Q&A over documents* | *Internal knowledge base assistant* |
| RAG + Fine-Tuning | *Domain-adapted responses with grounding* | *Legal document analysis with legal language style* |
| Knowledge Agent + RAG | *Complex reasoning over retrieved knowledge* | *Research assistant that searches, reads, and synthesizes* |
| Contact Center + RAG | *Support bot grounded in help docs* | *Customer support with product documentation lookup* |
| Recommendation + RAG | *Contextual recommendations with explanations* | *Product recommendations with detailed justifications* |
| Autonomous Workflow + Knowledge Agent | *End-to-end process with dynamic reasoning* | *Invoice processing: extract, validate, route, approve* |

## Notes

*Add your own observations about which patterns work best for your specific use case:*

- *Pattern chosen:*
- *Why:*
- *What I would do differently next time:*
