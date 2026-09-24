# System Design Template

## Requirements

### Functional Requirements

*What must the system do? List concrete, testable requirements.*

1. *The system shall [do X] when [condition Y]*
2. *Users must be able to [action]*
3. *The system shall integrate with [external system] to [purpose]*
4. *AI components shall [generate/classify/extract] [what] from [input]*
5. *...*

### Non-Functional Requirements

| Category | Requirement | Target |
|----------|-------------|--------|
| **Performance** | *Response time for AI queries* | *P95 < __ seconds* |
| **Availability** | *System uptime* | *__% (e.g., 99.9%)* |
| **Scalability** | *Concurrent users supported* | *__ users* |
| **Security** | *Data encryption standard* | *AES-256 at rest, TLS 1.3 in transit* |
| **Compliance** | *Regulatory requirements* | *e.g., SOC 2, HIPAA, GDPR* |
| **Cost** | *Monthly operating budget* | *$__ /month* |
| **Maintainability** | *Deployment frequency* | *e.g., Multiple times per day* |
| | | |

## High-Level Design

*Describe the overall architecture in 2-3 paragraphs. What are the major subsystems and how do they interact?*

```
┌─────────────────────────────────────────────────────────┐
│                    High-Level Architecture               │
│                                                          │
│   [Client Layer]  →  [API Layer]  →  [Service Layer]    │
│                                          ↓               │
│                                   [Data Layer]           │
│                                          ↓               │
│                                   [AI/ML Layer]          │
└─────────────────────────────────────────────────────────┘
```

*Replace with your actual high-level architecture diagram.*

## Component Details

### Component 1: *[Name]*

- **Responsibility:** *What does this component do?*
- **Technology:** *What is it built with?*
- **Interfaces:** *What APIs does it expose? What does it consume?*
- **Dependencies:** *What other components does it depend on?*
- **Scaling characteristics:** *How does it scale?*

### Component 2: *[Name]*

- **Responsibility:** *What does this component do?*
- **Technology:** *What is it built with?*
- **Interfaces:** *What APIs does it expose? What does it consume?*
- **Dependencies:** *What other components does it depend on?*
- **Scaling characteristics:** *How does it scale?*

### Component 3: *[Name]*

- **Responsibility:** *What does this component do?*
- **Technology:** *What is it built with?*
- **Interfaces:** *What APIs does it expose? What does it consume?*
- **Dependencies:** *What other components does it depend on?*
- **Scaling characteristics:** *How does it scale?*

*Add additional components as needed.*

## API Design

### Endpoint 1: *[Name]*

```
[METHOD] /api/v1/[resource]
```

- **Purpose:** *What does this endpoint do?*
- **Authentication:** *e.g., Bearer token, API key*
- **Request body:**
```json
{
  "field_1": "string — description",
  "field_2": 0
}
```
- **Response (200):**
```json
{
  "id": "string",
  "result": "string",
  "metadata": {}
}
```
- **Error responses:** *List common error codes and meanings*

### Endpoint 2: *[Name]*

```
[METHOD] /api/v1/[resource]
```

- **Purpose:** *What does this endpoint do?*
- **Authentication:** *e.g., Bearer token, API key*
- **Request body:**
```json
{
  "field_1": "string — description"
}
```
- **Response (200):**
```json
{
  "result": {}
}
```

*Add additional endpoints as needed.*

## Data Model

### Entity Relationship Diagram

```
┌──────────┐     ┌──────────────┐     ┌──────────┐
│  User    │────▶│  [Junction]  │◀────│  [Entity]│
│          │     │              │     │          │
│ id (PK)  │     │ user_id (FK) │     │ id (PK)  │
│ name     │     │ entity_id(FK)│     │ name     │
│ email    │     │ created_at   │     │ status   │
└──────────┘     └──────────────┘     └──────────┘
```

*Replace with your actual data model.*

### Key Entities

| Entity | Key Fields | Storage | Notes |
|--------|-----------|---------|-------|
| *e.g., User* | *id, name, email, role* | *PostgreSQL* | *Indexed on email* |
| *e.g., Document* | *id, content, embedding* | *PostgreSQL + Vector DB* | *Embedding generated on upload* |
| *e.g., Conversation* | *id, user_id, messages[]* | *PostgreSQL* | *Soft-deleted after 90 days* |
| *e.g., AuditLog* | *id, action, actor, timestamp* | *Append-only table* | *Never deleted* |
| | | | |

## Scalability

### Current Scale

- *Number of users: __*
- *Requests per second: __*
- *Data volume: __*
- *AI inference calls per day: __*

### Growth Projections

| Metric | Current | 6 Months | 12 Months | 24 Months |
|--------|---------|----------|-----------|-----------|
| *Users* | *__* | *__* | *__* | *__* |
| *Requests/sec* | *__* | *__* | *__* | *__* |
| *Data (GB)* | *__* | *__* | *__* | *__* |
| *AI cost/month* | *$__* | *$__* | *$__* | *$__* |

### Scaling Strategy

- **Horizontal scaling:** *Which components and how?*
- **Caching strategy:** *What gets cached and for how long?*
- **Database scaling:** *Read replicas, sharding, or partitioning plan*
- **AI scaling:** *Rate limiting, request queuing, caching predictions*

## Security

### Authentication and Authorization

- **Authentication method:** *e.g., OAuth 2.0, SAML, API keys*
- **Authorization model:** *e.g., RBAC, ABAC*
- **Session management:** *e.g., JWT with X-hour expiry*

### Data Protection

- **Encryption at rest:** *Algorithm and key management*
- **Encryption in transit:** *TLS version and certificate management*
- **PII handling:** *How personal data is stored, accessed, and deleted*
- **AI data considerations:** *How user data flows through AI models, data retention for training*

### Threat Mitigations

| Threat | Mitigation |
|--------|-----------|
| *Prompt injection* | *Input sanitization, output guardrails, system prompt hardening* |
| *Data exfiltration via AI* | *Output filtering, context window limits, access controls* |
| *Unauthorized access* | *MFA, role-based access, audit logging* |
| *DDoS* | *Rate limiting, WAF, CDN-level protection* |
| | |

## Monitoring

### Key Metrics

| Metric | Source | Alert Threshold | Dashboard |
|--------|--------|----------------|-----------|
| *Request latency (P50, P95, P99)* | *APM* | *P95 > __ ms* | *Operations* |
| *Error rate* | *Application logs* | *> __% over 5 min* | *Operations* |
| *AI response quality* | *Eval pipeline* | *Accuracy < __%* | *AI Metrics* |
| *Token usage / cost* | *AI provider API* | *> $__ /day* | *Cost* |
| *Uptime* | *Health checks* | *Any downtime* | *Status page* |
| | | | |

### Observability Stack

- **Metrics:** *e.g., Prometheus + Grafana / Datadog*
- **Logging:** *e.g., ELK Stack / Datadog Logs*
- **Tracing:** *e.g., Jaeger / Datadog APM*
- **AI-specific:** *e.g., LangSmith / custom eval dashboard*

## Trade-Offs

*Document the key trade-offs in this design and why you made the choices you did.*

| Trade-Off | Option A (Chosen) | Option B (Rejected) | Rationale |
|-----------|-------------------|---------------------|-----------|
| *e.g., Consistency vs. availability* | *Strong consistency* | *Eventual consistency* | *Financial data requires accuracy over availability* |
| *e.g., Build vs. buy* | *Managed service* | *Self-hosted* | *Team size too small for operational burden* |
| *e.g., Latency vs. accuracy* | *Cached responses* | *Real-time inference* | *Acceptable staleness for 80% of queries* |
| | | | |

## Open Questions

- *List any unresolved questions or decisions that need further investigation*
- *e.g., Should we use streaming responses for the AI endpoint?*
- *e.g., What is the right cache TTL for AI-generated content?*
- *e.g., Do we need a separate service for [X] or can it be part of [Y]?*
