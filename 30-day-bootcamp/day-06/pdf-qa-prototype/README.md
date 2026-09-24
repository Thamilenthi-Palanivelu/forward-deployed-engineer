# PDF Q&A Prototype

**Date:** *YYYY-MM-DD*

---

## Problem Statement

*What problem does this prototype solve? Who is the user? Why does a PDF Q&A tool matter in the context of FDE work?*

*Your problem statement here*

---

## Architecture

*Describe the end-to-end architecture of your PDF Q&A system.*

```
[PDF Upload]
    |
    v
[Step 1: ___] --> [Step 2: ___] --> [Step 3: ___]
    |                                      |
    v                                      v
[Storage: ___]                     [Response to User]
```

*Replace the diagram above with your actual architecture. Include components like PDF parsing, chunking, embedding, vector storage, retrieval, and generation.*

### Component Breakdown

| Component | Purpose | Technology Used |
|-----------|---------|-----------------|
| PDF Parser | *extract text from PDFs* | *e.g., PyPDF2, pdfplumber* |
| Text Chunker | *split text into retrievable segments* | *e.g., LangChain splitters, custom* |
| Embedding Model | *convert text to vectors* | *e.g., OpenAI embeddings, sentence-transformers* |
| Vector Store | *store and retrieve embeddings* | *e.g., ChromaDB, FAISS, Pinecone* |
| LLM | *generate answers from context* | *e.g., GPT-4, Claude* |
| *Additional* | *purpose* | *technology* |

---

## Tech Stack

- **Language:** *e.g., Python 3.11*
- **Framework:** *e.g., LangChain, LlamaIndex, custom*
- **Vector database:** *your choice*
- **LLM provider:** *your choice*
- **Frontend (if any):** *e.g., Streamlit, Gradio, CLI only*

---

## Setup Instructions

```bash
# Step 1: Clone / navigate to this directory

# Step 2: Create virtual environment

# Step 3: Install dependencies

# Step 4: Set environment variables

# Step 5: Run the application
```

*Provide the exact commands someone needs to run your prototype.*

---

## Demo

*Document a demo of your prototype. Show the input and output.*

### Example 1

**PDF used:** *name or description of the PDF*

**Question:** *"your question"*

**Answer:** *the generated answer*

**Source chunks used:** *which parts of the document were retrieved*

### Example 2

**PDF used:** *name or description of the PDF*

**Question:** *"your question"*

**Answer:** *the generated answer*

**Source chunks used:** *which parts of the document were retrieved*

---

## Known Limitations

*Be upfront about what does not work well.*

- *Limitation 1: e.g., struggles with tables and charts in PDFs*
- *Limitation 2: e.g., large PDFs exceed context window*
- *Limitation 3: e.g., no support for multi-PDF queries*
- *Limitation 4*
