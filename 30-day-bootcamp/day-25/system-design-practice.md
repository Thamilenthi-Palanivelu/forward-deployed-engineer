# System Design Practice

**Date:** *YYYY-MM-DD*

**Problem Number/Title:** *e.g., Problem 3: Design a Real-Time Analytics Dashboard*

*Use this template for each system design problem you practice. Complete one per session.*

---

## Problem Statement

*Write or paste the system design question here.*

---

## Clarifying Questions Asked

1. *What is the expected scale? (users, requests per second, data volume)*
2. *What are the latency requirements? (real-time vs. near-real-time vs. batch)*
3. *Who are the end users and what are their primary workflows?*
4. *What is the read-to-write ratio?*
5. *Are there any existing systems or constraints we need to integrate with?*
6. *What are the data retention and compliance requirements?*
7. *What is the budget or infrastructure preference? (cloud provider, on-prem, hybrid)*
8. *What does failure look like? What is the acceptable level of downtime?*

---

## Requirements

### Functional Requirements

- *Requirement 1: The system must...*
- *Requirement 2: Users should be able to...*
- *Requirement 3: The system must support...*
- *Requirement 4: ...*

### Non-Functional Requirements

- *Performance: Response time under [N]ms for [operation]*
- *Scalability: Support [N] concurrent users / [N] requests per second*
- *Availability: [N]% uptime SLA*
- *Security: [Authentication, encryption, compliance requirements]*
- *Maintainability: [Deployment, monitoring, observability requirements]*

---

## High-Level Design

*Describe your high-level architecture in 3-5 sentences. Sketch the major components and how they interact. Identify the data flow from ingestion to serving.*

*Draw or describe the architecture diagram here. Include: client layer, API gateway, core services, data stores, and any async processing layers.*

---

## Component Deep Dive

| Component | Technology Choice | Rationale | Alternatives Considered |
|---|---|---|---|
| *API Gateway* | *e.g., Kong, AWS API Gateway* | *Why this choice fits the requirements* | *Other options you evaluated* |
| *Application Server* | *e.g., Node.js, Go, Python/FastAPI* | *Why this choice fits the requirements* | *Other options you evaluated* |
| *Primary Database* | *e.g., PostgreSQL, DynamoDB* | *Why this choice fits the requirements* | *Other options you evaluated* |
| *Cache Layer* | *e.g., Redis, Memcached* | *Why this choice fits the requirements* | *Other options you evaluated* |
| *Message Queue* | *e.g., Kafka, SQS, RabbitMQ* | *Why this choice fits the requirements* | *Other options you evaluated* |
| *Search/Analytics* | *e.g., Elasticsearch, ClickHouse* | *Why this choice fits the requirements* | *Other options you evaluated* |

---

## Data Model

*Describe key entities and their relationships.*

| Entity | Key Fields | Relationships |
|---|---|---|
| *Entity 1 (e.g., User)* | *id, name, email, created_at* | *Has many [Entity 2]* |
| *Entity 2 (e.g., Project)* | *id, owner_id, name, status* | *Belongs to [Entity 1], has many [Entity 3]* |
| *Entity 3 (e.g., Event)* | *id, project_id, type, payload, timestamp* | *Belongs to [Entity 2]* |
| *Entity 4* | *...* | *...* |

---

## API Design

*Define the core API endpoints.*

| Endpoint | Method | Request | Response | Notes |
|---|---|---|---|---|
| */api/v1/resource* | *GET* | *Query params: limit, offset, filters* | *200: List of resources with pagination* | *Supports cursor-based pagination* |
| */api/v1/resource* | *POST* | *Body: { name, config, ... }* | *201: Created resource object* | *Idempotent with client-supplied key* |
| */api/v1/resource/:id* | *GET* | *Path param: id* | *200: Single resource object* | *Cached with [TTL]* |
| */api/v1/resource/:id* | *PUT* | *Body: { updated fields }* | *200: Updated resource object* | *Optimistic locking via ETag* |
| */api/v1/resource/:id* | *DELETE* | *Path param: id* | *204: No content* | *Soft delete with retention policy* |

---

## Scalability Considerations

1. *How will you handle a 10x increase in traffic? (horizontal scaling, auto-scaling groups, load balancing)*
2. *How will you partition or shard the data? (by tenant, by geography, by time range)*
3. *What caching strategy will you use? (cache-aside, write-through, TTL policy)*
4. *How will you handle hot spots or uneven load distribution?*
5. *What is your approach to database read replicas and connection pooling?*

---

## Trade-Offs Discussed

| Decision | Option A | Option B | Choice Made | Reasoning |
|---|---|---|---|---|
| *Database type* | *SQL (strong consistency)* | *NoSQL (flexible schema, horizontal scale)* | *Your choice* | *Why this trade-off makes sense for the requirements* |
| *Communication pattern* | *Synchronous (REST/gRPC)* | *Asynchronous (event-driven)* | *Your choice* | *Why this trade-off makes sense for the requirements* |
| *Consistency model* | *Strong consistency* | *Eventual consistency* | *Your choice* | *Why this trade-off makes sense for the requirements* |
| *Deployment model* | *Monolith* | *Microservices* | *Your choice* | *Why this trade-off makes sense for the requirements* |

---

## Talking Points Used

*Key phrases and frameworks you used during the walkthrough.*

- *"Let me start by clarifying the requirements..."*
- *"The key trade-off here is between [X] and [Y]..."*
- *"At this scale, the bottleneck will be..."*
- *"I would instrument this with [monitoring approach] to catch..."*
- *"If we needed to evolve this system, the next step would be..."*
- *Add your own phrases that felt effective or that you want to practice.*

---

## Self-Evaluation

| Dimension | Score (1-5) | Notes |
|---|---|---|
| Clarity | *__/5* | *Was your explanation easy to follow? Did you use diagrams and structure effectively?* |
| Depth | *__/5* | *Did you go deep enough on the critical components? Did you avoid hand-waving?* |
| Trade-off Analysis | *__/5* | *Did you identify and articulate meaningful trade-offs? Did you justify your choices?* |
| Communication | *__/5* | *Did you check in with the interviewer? Did you manage the conversation well?* |
| Time Management | *__/5* | *Did you allocate time well across sections? Did you cover all major areas?* |
