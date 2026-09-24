# Claims Processing Pipeline

## Overview

*Brief description of the claims processing pipeline project.*

*e.g., "An AI-powered claims processing pipeline that automates document classification, data extraction, and routing for insurance claims. The system reduces manual processing time by automating repetitive steps while maintaining human oversight for complex or low-confidence cases."*

| | |
|---|---|
| **Status** | *In Development / Pilot / Production* |
| **Owner** | *Your name* |
| **Repository** | *Link to repo* |
| **Documentation** | *Link to additional docs* |
| **Environment** | *Dev: [URL] / Staging: [URL] / Prod: [URL]* |

## Architecture

*See [architecture.md](./architecture.md) for detailed architecture documentation.*

```
Documents → Ingestion → Classification → Extraction → Claims System
                              ↓ (low confidence)
                        Human Review
```

### Tech Stack

| Layer | Technology |
|-------|-----------|
| **Backend** | *e.g., Python 3.11 / FastAPI* |
| **Frontend (Review UI)** | *e.g., React / Next.js* |
| **Database** | *e.g., PostgreSQL 15* |
| **Document Storage** | *e.g., AWS S3 / GCP Cloud Storage* |
| **AI/ML** | *e.g., Claude API for classification and extraction* |
| **OCR** | *e.g., Tesseract / AWS Textract / Google Document AI* |
| **Message Queue** | *e.g., RabbitMQ / SQS / Redis* |
| **Monitoring** | *e.g., Datadog / Grafana + Prometheus* |
| **CI/CD** | *e.g., GitHub Actions / GitLab CI* |

## Setup

### Prerequisites

```
- Python >= 3.10
- Node.js >= 18 (for review UI)
- PostgreSQL >= 14
- Docker & Docker Compose
- API keys: [list required keys]
```

### Quick Start

```bash
# 1. Clone the repository
git clone [repo-url]
cd claims-processing

# 2. Copy environment configuration
cp .env.example .env
# Edit .env with your API keys and database credentials

# 3. Start infrastructure (database, queue, etc.)
docker-compose up -d

# 4. Install Python dependencies
python -m venv venv
source venv/bin/activate
pip install -r requirements.txt

# 5. Run database migrations
python manage.py migrate

# 6. Start the processing pipeline
python manage.py start-workers

# 7. Start the API server
uvicorn app.main:app --reload --port 8000

# 8. (Optional) Start the review UI
cd frontend && npm install && npm run dev
```

### Environment Variables

| Variable | Required | Description | Example |
|----------|----------|-------------|---------|
| `DATABASE_URL` | Yes | *PostgreSQL connection string* | `postgresql://user:pass@localhost:5432/claims` |
| `AI_API_KEY` | Yes | *AI provider API key* | `sk-...` |
| `AI_MODEL` | No | *Model to use for classification/extraction* | `claude-sonnet-4-20250514` |
| `S3_BUCKET` | Yes | *Document storage bucket* | `claims-documents-dev` |
| `CONFIDENCE_THRESHOLD` | No | *Min confidence for auto-routing (default: 0.85)* | `0.85` |
| `MAX_CONCURRENT_WORKERS` | No | *Number of processing workers (default: 4)* | `4` |
| `LOG_LEVEL` | No | *Logging verbosity (default: INFO)* | `INFO` |
| | | | |

## Usage

### Processing a Claim

#### Via API

```bash
# Upload a claim document for processing
curl -X POST http://localhost:8000/api/v1/claims \
  -H "Authorization: Bearer $TOKEN" \
  -F "file=@claim-document.pdf" \
  -F "source=manual_upload"
```

**Response:**
```json
{
  "claim_id": "clm_abc123",
  "status": "processing",
  "submitted_at": "2025-01-15T10:30:00Z",
  "estimated_completion": "2025-01-15T10:31:00Z"
}
```

#### Check Claim Status

```bash
curl http://localhost:8000/api/v1/claims/clm_abc123 \
  -H "Authorization: Bearer $TOKEN"
```

**Response:**
```json
{
  "claim_id": "clm_abc123",
  "status": "completed",
  "classification": {
    "type": "medical",
    "confidence": 0.94
  },
  "extraction": {
    "patient_name": "...",
    "date_of_service": "...",
    "provider_npi": "...",
    "billed_amount": "...",
    "fields_extracted": 12,
    "fields_requiring_review": 0
  },
  "routing": "auto_processed",
  "processed_at": "2025-01-15T10:30:45Z"
}
```

### Batch Processing

```bash
# Process a directory of claim documents
python scripts/batch_process.py --input-dir ./claims/ --output-dir ./results/
```

### Human Review

*Access the review interface at [http://localhost:3000](http://localhost:3000) to review claims flagged for manual verification.*

## Sample Data

### Test Documents

*Sample claim documents for testing are located in `tests/fixtures/`.*

| File | Claim Type | Expected Classification | Notes |
|------|-----------|------------------------|-------|
| `sample_medical_1.pdf` | *Medical (CMS-1500)* | *medical, confidence > 0.9* | *Standard medical claim* |
| `sample_dental_1.pdf` | *Dental (ADA)* | *dental, confidence > 0.9* | *Routine dental claim* |
| `sample_complex_1.pdf` | *Medical (complex)* | *medical, may require review* | *Multi-page, handwritten notes* |
| `sample_blurry_1.pdf` | *Unknown* | *Low confidence, route to review* | *Tests OCR quality handling* |

### Generating Test Data

```bash
# Generate synthetic claim documents for testing
python scripts/generate_test_data.py --count 100 --types medical,dental,vision
```

## API Reference

### Endpoints

| Method | Path | Description | Auth |
|--------|------|-------------|------|
| `POST` | `/api/v1/claims` | *Submit a claim for processing* | *Bearer token* |
| `GET` | `/api/v1/claims/:id` | *Get claim status and results* | *Bearer token* |
| `GET` | `/api/v1/claims` | *List claims (with filters)* | *Bearer token* |
| `PATCH` | `/api/v1/claims/:id/review` | *Submit human review decision* | *Bearer token (reviewer role)* |
| `GET` | `/api/v1/claims/queue` | *Get human review queue* | *Bearer token (reviewer role)* |
| `GET` | `/api/v1/metrics` | *Get processing metrics* | *Bearer token (admin role)* |
| `GET` | `/api/v1/health` | *Health check* | *None* |

### Error Codes

| Code | Meaning | Common Cause |
|------|---------|-------------|
| `400` | *Bad Request* | *Invalid file format, missing required fields* |
| `401` | *Unauthorized* | *Missing or invalid authentication token* |
| `403` | *Forbidden* | *Insufficient permissions for the requested action* |
| `404` | *Not Found* | *Claim ID does not exist* |
| `413` | *Payload Too Large* | *Document exceeds maximum file size* |
| `429` | *Too Many Requests* | *Rate limit exceeded* |
| `500` | *Internal Server Error* | *Processing failure, AI API error* |
| `503` | *Service Unavailable* | *System overloaded or in maintenance* |

## Testing

### Run All Tests

```bash
# Unit tests
pytest tests/unit/ -v

# Integration tests (requires running infrastructure)
pytest tests/integration/ -v

# AI evaluation tests (requires API key)
pytest tests/eval/ -v

# All tests with coverage
pytest --cov=app --cov-report=html
```

### Test Categories

| Category | Directory | What It Tests | Requires |
|----------|-----------|--------------|----------|
| *Unit* | `tests/unit/` | *Business logic, validators, utilities* | *Nothing (mocked)* |
| *Integration* | `tests/integration/` | *API endpoints, database, queue* | *Docker services* |
| *Evaluation* | `tests/eval/` | *AI accuracy, extraction quality* | *AI API key* |
| *End-to-end* | `tests/e2e/` | *Full pipeline with sample docs* | *All services running* |

### AI Evaluation

*See [../../day-16/rag-evaluation.md](../../day-16/rag-evaluation.md) for the evaluation framework. Adapt for claims-specific metrics.*

```bash
# Run claims-specific evaluation
python scripts/evaluate.py --test-set tests/eval/claims_test_set.json --output results/eval_report.json
```
