# RAG Evaluation Results

## Evaluation Summary

- **Date:** *YYYY-MM-DD*
- **Pipeline version:** *e.g., v0.1*
- **Number of test queries:** *__*
- **Embedding model:** *e.g., text-embedding-3-small*
- **LLM:** *e.g., Claude Sonnet*
- **Vector store:** *e.g., Chroma / Pinecone*
- **Top-k retrieval:** *__*
- **Chunk size:** *__ tokens*

## Detailed Results

| # | Query | Expected Answer | Retrieved Context (Relevant?) | Generated Answer | Accuracy Score (1-5) | Notes |
|---|-------|-----------------|-------------------------------|------------------|---------------------|-------|
| 1 | *e.g., "What is the refund policy?"* | *e.g., "Refunds are available within 30 days of purchase..."* | *e.g., "Chunk from refund-policy.md, Section 3.2" (Yes)* | *e.g., "Based on the documentation, refunds are..."* | *e.g., 5* | *e.g., Exact match with source* |
| 2 | *e.g., "How do I configure SSO?"* | *e.g., "Navigate to Settings > Security > SSO..."* | *e.g., "Chunk from admin-guide.md, Section 7.1" (Yes)* | *e.g., "To configure SSO, go to..."* | *e.g., 4* | *e.g., Correct but missed one step* |
| 3 | *e.g., "What databases are supported?"* | *e.g., "PostgreSQL, MySQL, and MongoDB"* | *e.g., "Chunk from requirements.md" (Partial)* | *e.g., "The system supports PostgreSQL and MySQL"* | *e.g., 3* | *e.g., Missed MongoDB, chunk was partially relevant* |
| 4 | *e.g., "Who is the CEO?"* | *e.g., Not in documents* | *e.g., "Chunk from about-us.md" (No)* | *e.g., "I don't have that information..."* | *e.g., 5* | *e.g., Correctly refused to answer* |
| 5 | | | | | | |
| 6 | | | | | | |
| 7 | | | | | | |
| 8 | | | | | | |
| 9 | | | | | | |
| 10 | | | | | | |
| 11 | | | | | | |
| 12 | | | | | | |
| 13 | | | | | | |
| 14 | | | | | | |
| 15 | | | | | | |

**Accuracy Score Key:**
- **5** = Perfect answer, fully grounded in source material
- **4** = Correct answer with minor omissions or imprecise language
- **3** = Partially correct, missing important details
- **2** = Mostly incorrect or misleading
- **1** = Completely wrong or hallucinated

## Overall Accuracy

| Metric | Value | Target | Status |
|--------|-------|--------|--------|
| **Retrieval precision** (relevant chunks in top-k) | *__% (* /__ queries)* | *> 80%* | *On track / Needs improvement* |
| **Retrieval recall** (answer findable in corpus) | *__% (* /__ queries)* | *> 90%* | *On track / Needs improvement* |
| **Answer accuracy** (score >= 4) | *__% (* /__ queries)* | *> 85%* | *On track / Needs improvement* |
| **Hallucination rate** (unsupported claims) | *__% (* /__ queries)* | *< 5%* | *On track / Needs improvement* |
| **Refusal accuracy** (correctly says "I don't know") | *__% (* /__ queries)* | *> 90%* | *On track / Needs improvement* |
| **Average latency** | *__ ms* | *< 3000 ms* | *On track / Needs improvement* |
| **Average cost per query** | *$__* | *< $0.05* | *On track / Needs improvement* |

## Failure Analysis

### Retrieval Failures

*Analyze cases where the wrong chunks were retrieved.*

| Query # | Root Cause | Potential Fix |
|---------|-----------|---------------|
| *e.g., #3* | *e.g., Relevant content split across chunk boundary* | *e.g., Increase chunk overlap or use semantic chunking* |
| *e.g., #7* | *e.g., Query uses different terminology than docs* | *e.g., Add synonym expansion or query rewriting* |
| | | |

### Generation Failures

*Analyze cases where retrieval was correct but the generated answer was wrong.*

| Query # | Root Cause | Potential Fix |
|---------|-----------|---------------|
| *e.g., #5* | *e.g., Model ignored relevant context in favor of parametric knowledge* | *e.g., Strengthen system prompt to prioritize retrieved context* |
| *e.g., #8* | *e.g., Context was too long and answer was buried* | *e.g., Re-rank chunks to put most relevant first* |
| | | |

### Categories of Errors

| Error Type | Count | Percentage | Example |
|-----------|-------|------------|---------|
| *Wrong retrieval* | *__* | *__%* | *Query #__* |
| *Incomplete answer* | *__* | *__%* | *Query #__* |
| *Hallucination* | *__* | *__%* | *Query #__* |
| *Failed to refuse* | *__* | *__%* | *Query #__* |
| *Incorrect refusal* | *__* | *__%* | *Query #__* |

## Improvement Ideas

*Based on the evaluation results, prioritize improvements.*

| Priority | Improvement | Expected Impact | Effort |
|----------|------------|-----------------|--------|
| **P0** | *e.g., Increase chunk overlap to 100 tokens* | *Fix ~3 retrieval failures* | *Low (config change)* |
| **P1** | *e.g., Add re-ranking with cross-encoder* | *Improve retrieval precision by ~10%* | *Medium (new component)* |
| **P1** | *e.g., Implement query rewriting* | *Handle terminology mismatches* | *Medium (prompt engineering)* |
| **P2** | *e.g., Switch to semantic chunking* | *Better chunk boundaries* | *High (re-index all docs)* |
| **P2** | *e.g., Add hybrid search (BM25 + semantic)* | *Improve recall for keyword queries* | *High (infrastructure change)* |
| | | | |

## Next Steps

- [ ] *Implement P0 improvements and re-evaluate*
- [ ] *Expand test set to __ queries covering more edge cases*
- [ ] *Add automated evaluation to CI/CD pipeline*
- [ ] *Set up monitoring for production query quality*
