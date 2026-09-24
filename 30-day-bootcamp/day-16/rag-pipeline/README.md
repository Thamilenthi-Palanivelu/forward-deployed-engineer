# RAG Pipeline Project

## Overview

*Describe what this RAG pipeline does, what problem it solves, and who it serves.*

- **Purpose:** *e.g., Answer employee questions using internal documentation*
- **Target users:** *e.g., Internal engineering team, customer support agents*
- **Source documents:** *e.g., Confluence pages, PDF manuals, API documentation*
- **Expected query types:** *e.g., "How do I configure X?", "What is the policy for Y?"*

## Architecture

```
┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│  Documents   │────▶│  Chunking &  │────▶│  Vector      │
│  (Source)    │     │  Embedding   │     │  Store       │
└──────────────┘     └──────────────┘     └──────┬───────┘
                                                  │
┌──────────────┐     ┌──────────────┐             │
│  Response    │◀────│  LLM         │◀────────────┘
│  (Output)   │     │  Generation  │     Retrieval
└──────────────┘     └──────────────┘
```

*Modify this diagram to reflect your actual pipeline architecture.*

### Design Decisions

- **Chunking strategy:** *e.g., Recursive character splitting, 512 tokens, 50-token overlap*
- **Embedding model:** *e.g., text-embedding-3-small, 1536 dimensions*
- **Vector store:** *e.g., Pinecone, Weaviate, Chroma, pgvector*
- **LLM for generation:** *e.g., Claude Sonnet, GPT-4o*
- **Retrieval method:** *e.g., Cosine similarity, top-k=5, with MMR re-ranking*

## Components

### 1. Document Ingestion

- **Supported formats:** *e.g., PDF, Markdown, HTML, plain text*
- **Preprocessing steps:** *e.g., Extract text, remove headers/footers, normalize whitespace*
- **Metadata extraction:** *e.g., Title, source URL, last updated date, section headers*

### 2. Chunking & Embedding

- **Chunking method:** *e.g., RecursiveCharacterTextSplitter*
- **Chunk size:** *__ tokens/characters*
- **Chunk overlap:** *__ tokens/characters*
- **Embedding model:** *Model name and provider*
- **Embedding dimensions:** *__*
- **Batch size:** *__ documents per batch*

### 3. Vector Store

- **Provider:** *e.g., Pinecone, Chroma, Weaviate*
- **Index configuration:** *e.g., Metric: cosine, Pod type: p1.x1*
- **Namespace strategy:** *e.g., One namespace per document source*
- **Metadata stored:** *e.g., source, page_number, section, last_updated*

### 4. Retrieval

- **Search method:** *e.g., Similarity search with score threshold*
- **Top-k:** *Number of chunks retrieved*
- **Re-ranking:** *e.g., Cohere re-ranker, cross-encoder, MMR*
- **Filters:** *e.g., Metadata filters for source type, date range*
- **Hybrid search:** *If using keyword + semantic, describe the fusion method*

### 5. Generation

- **LLM:** *Model name and provider*
- **System prompt:** *Summarize the system prompt strategy (full prompt in separate file if long)*
- **Context window usage:** *How retrieved chunks are formatted and injected*
- **Citation strategy:** *How sources are attributed in responses*
- **Guardrails:** *e.g., "I don't know" for low-confidence, source verification*

## Setup

### Prerequisites

```
- Python >= 3.10
- API keys: [list required API keys]
- Vector store account/instance
```

### Installation

```bash
# Clone the repository
# git clone [repo-url]

# Install dependencies
# pip install -r requirements.txt

# Set environment variables
# cp .env.example .env
# Edit .env with your API keys
```

### Configuration

*Describe key configuration options and where they live.*

| Config | File/Env Var | Default | Description |
|--------|-------------|---------|-------------|
| *Chunk size* | *config.yaml* | *512* | *Token count per chunk* |
| *Top-k retrieval* | *config.yaml* | *5* | *Number of chunks to retrieve* |
| *LLM model* | *.env* | *claude-sonnet-4-20250514* | *Model for generation* |
| *Embedding model* | *.env* | *text-embedding-3-small* | *Model for embeddings* |
| | | | |

## Usage

### Indexing Documents

```bash
# Index a directory of documents
# python index.py --source ./documents/

# Index a single file
# python index.py --file ./documents/manual.pdf
```

### Querying

```bash
# Interactive query mode
# python query.py

# Single query
# python query.py --query "How do I reset my password?"
```

### API (if applicable)

```bash
# Start the API server
# python api.py

# Query via API
# curl -X POST http://localhost:8000/query \
#   -H "Content-Type: application/json" \
#   -d '{"query": "How do I reset my password?"}'
```

## Evaluation Results

*Summary of evaluation results. See `../rag-evaluation.md` for detailed results.*

| Metric | Score | Target |
|--------|-------|--------|
| *Retrieval accuracy (relevant in top-k)* | *__%* | *> 80%* |
| *Answer accuracy* | *__%* | *> 85%* |
| *Hallucination rate* | *__%* | *< 5%* |
| *Average latency* | *__ ms* | *< 3000 ms* |
| *Cost per query* | *$__* | *< $0.05* |

## Known Limitations

- *List known limitations of the current pipeline*
- *e.g., Does not handle tables/images in PDFs well*
- *e.g., Performance degrades with queries spanning multiple documents*
- *e.g., No support for real-time document updates yet*

## Future Improvements

- [ ] *e.g., Add hybrid search (keyword + semantic)*
- [ ] *e.g., Implement query decomposition for complex questions*
- [ ] *e.g., Add feedback loop for continuous improvement*
- [ ] *e.g., Support streaming responses*
