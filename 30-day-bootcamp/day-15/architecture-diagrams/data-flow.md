# Data Flow Diagram

## Data Sources

*Identify all sources of data entering the system.*

| Source | Data Type | Format | Volume | Frequency |
|--------|-----------|--------|--------|-----------|
| *e.g., User input* | *Text queries, form submissions* | *JSON* | *~1K requests/day* | *Real-time* |
| *e.g., Document uploads* | *PDFs, Word docs* | *Binary/multipart* | *~100 docs/day* | *On-demand* |
| *e.g., External API* | *Customer records* | *REST/JSON* | *~10K records* | *Daily batch sync* |
| *e.g., Event stream* | *User activity events* | *Protobuf/Avro* | *~50K events/day* | *Continuous* |
| | | | | |
| | | | | |

## Processing Steps

*Document each stage of data transformation from ingestion to output.*

### Step 1: Ingestion
- **Input:** *Raw data from sources listed above*
- **Processing:** *Validation, sanitization, format normalization*
- **Output:** *Cleaned, structured data ready for processing*
- **Error handling:** *What happens when ingestion fails?*

### Step 2: Enrichment / Transformation
- **Input:** *Cleaned data from Step 1*
- **Processing:** *e.g., Embedding generation, feature extraction, classification*
- **Output:** *Enriched data with AI-generated metadata*
- **Error handling:** *Fallback when AI processing fails?*

### Step 3: AI Processing
- **Input:** *Enriched data, user query/context*
- **Processing:** *e.g., RAG retrieval, prompt construction, model inference*
- **Output:** *AI-generated response, confidence scores*
- **Error handling:** *Retry policy, fallback responses*

### Step 4: Post-Processing
- **Input:** *Raw AI output*
- **Processing:** *e.g., Response formatting, guardrail checks, citation attachment*
- **Output:** *Final validated response*
- **Error handling:** *Content filtering, safety checks*

*Add or remove steps as needed for your system.*

## Storage

| Store | Purpose | Data Retained | Retention Policy |
|-------|---------|---------------|------------------|
| *e.g., PostgreSQL* | *User accounts, app state* | *Structured records* | *Indefinite* |
| *e.g., Vector DB (Pinecone/Weaviate)* | *Document embeddings for RAG* | *Vectors + metadata* | *Until re-indexed* |
| *e.g., S3/GCS* | *Raw document storage* | *Uploaded files* | *90 days* |
| *e.g., Redis* | *Session cache, recent queries* | *Key-value pairs* | *TTL: 24 hours* |
| *e.g., Logging (ELK/Datadog)* | *Audit trail, debugging* | *Logs, traces* | *30 days* |
| | | | |

## Output / Consumption

*How is processed data delivered to end users or downstream systems?*

| Consumer | Delivery Method | Format | SLA |
|----------|----------------|--------|-----|
| *e.g., Web frontend* | *REST API response* | *JSON* | *P95 < 2s* |
| *e.g., Mobile app* | *REST API / WebSocket* | *JSON / SSE* | *P95 < 3s* |
| *e.g., Analytics pipeline* | *Event stream* | *Parquet/JSON* | *< 5 min delay* |
| *e.g., Reporting dashboard* | *Scheduled query* | *CSV/SQL* | *Daily refresh* |
| | | | |

## Data Flow Diagram

*Replace the placeholder below with your data flow diagram.*

```
┌──────────┐    ┌───────────┐    ┌──────────────┐    ┌────────────┐
│  Data     │───▶│ Ingestion │───▶│ Enrichment / │───▶│    AI      │
│  Sources  │    │ & Cleanup │    │ Transform    │    │ Processing │
└──────────┘    └───────────┘    └──────────────┘    └─────┬──────┘
                                                           │
                     ┌─────────────────────────────────────┘
                     ▼
              ┌──────────────┐    ┌──────────────┐    ┌────────────┐
              │    Post-     │───▶│   Storage    │───▶│  Output /  │
              │  Processing  │    │              │    │ Consumers  │
              └──────────────┘    └──────────────┘    └────────────┘
```

*Modify this diagram to show your actual data flow. Include branching paths, feedback loops, and error flows where applicable.*

## Data Sensitivity Classification

| Data Element | Classification | Encryption | Access Control |
|-------------|---------------|------------|----------------|
| *e.g., User PII* | *Confidential* | *At rest + in transit* | *Role-based, need-to-know* |
| *e.g., AI prompts/responses* | *Internal* | *In transit* | *Application-level* |
| *e.g., Aggregated metrics* | *Public* | *In transit* | *Read-only dashboard* |
| | | | |
