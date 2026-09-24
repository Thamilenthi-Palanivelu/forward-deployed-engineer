# Requirements-to-Technology Mapping

> Use this document to translate business requirements into technical decisions. It ensures every feature has a clear technical path and helps identify gaps, dependencies, and complexity early.

---

## How to Use This Template

1. Start with the **Business Requirement** column -- these come from discovery and the solution brief
2. Identify the **Technical Capability** needed to fulfill each requirement
3. Map to specific **Technology/Tool** choices
4. Assess **Complexity** honestly (High/Medium/Low)
5. Identify **Dependencies** -- what must be true or available before you can build this
6. Add **Notes** for context, risks, or alternatives considered

---

## Requirements Map

| #  | Business Requirement | Technical Capability Needed | Technology / Tool | Complexity (H/M/L) | Dependencies | Notes |
|----|----------------------|-----------------------------|-------------------|---------------------|--------------|-------|
| 1  | *[e.g., "See shipment location in real time"]* | *[e.g., "Ingest GPS data streams, geocode locations, render on map"]* | *[e.g., "Kafka for streaming, Mapbox for rendering"]* | *[e.g., M]* | *[e.g., "GPS feed API access from carrier"]* | *[e.g., "Carrier provides updates every 5 min, not true real-time"]*  |
| 2  | *[e.g., "Get notified when shipment is delayed"]* | *[e.g., "Event detection, notification dispatch"]* | *[e.g., "Python rules engine, Twilio for SMS, SES for email"]* | *[e.g., L]* | *[e.g., "Customer contact list, delay threshold definition"]* | *[e.g., "Start with email only; add SMS in Phase 2"]* |
| 3  | *[e.g., "Search for any shipment by tracking number"]* | *[e.g., "Full-text search across shipment records"]* | *[e.g., "Elasticsearch or PostgreSQL full-text"]* | *[e.g., L]* | *[e.g., "Unified data model for shipments"]* | *[e.g., "Postgres is sufficient at current volume"]* |
| 4  | *[Business requirement]* | *[Technical capability]* | *[Technology]* | *[H/M/L]* | *[Dependencies]* | *[Notes]* |
| 5  | *[Business requirement]* | *[Technical capability]* | *[Technology]* | *[H/M/L]* | *[Dependencies]* | *[Notes]* |
| 6  | *[Business requirement]* | *[Technical capability]* | *[Technology]* | *[H/M/L]* | *[Dependencies]* | *[Notes]* |
| 7  | *[Business requirement]* | *[Technical capability]* | *[Technology]* | *[H/M/L]* | *[Dependencies]* | *[Notes]* |
| 8  | *[Business requirement]* | *[Technical capability]* | *[Technology]* | *[H/M/L]* | *[Dependencies]* | *[Notes]* |

---

## Non-Functional Requirements

| #  | Requirement            | Specification                         | Technology / Approach            | Complexity | Notes                      |
|----|------------------------|---------------------------------------|----------------------------------|------------|----------------------------|
| 1  | *[e.g., "Performance"]* | *[e.g., "Dashboard loads in < 2 sec"]* | *[e.g., "CDN, query optimization"]* | *[M]* | *[e.g., "Test with 10K concurrent shipments"]* |
| 2  | *[e.g., "Security"]*   | *[e.g., "SSO integration, encrypted at rest"]* | *[e.g., "SAML/OIDC, AES-256"]* | *[M]* | *[e.g., "Client uses Okta"]* |
| 3  | *[e.g., "Scalability"]* | *[e.g., "Handle 10x current volume"]* | *[e.g., "Horizontal scaling, queue-based"]* | *[H]* | *[e.g., "Not needed for POC, but architect for it"]* |
| 4  | *[Requirement]*        | *[Specification]*                     | *[Technology]*                   | *[H/M/L]* | *[Notes]*                  |

---

## Technology Stack Summary

*Roll up the individual choices into a coherent stack.*

| Layer               | Technology                   | Rationale                                     |
|---------------------|------------------------------|-----------------------------------------------|
| Frontend            | *[e.g., "React + TypeScript"]* | *[e.g., "Client team already uses React"]*  |
| Backend API         | *[e.g., "Python / FastAPI"]* | *[e.g., "Fast to prototype, good async support"]* |
| Database            | *[e.g., "PostgreSQL"]*      | *[e.g., "Reliable, client already runs it"]* |
| Message Queue       | *[e.g., "Redis Streams"]*   | *[e.g., "Lightweight, sufficient for POC volume"]* |
| Infrastructure      | *[e.g., "AWS (client's cloud)"]* | *[e.g., "Matches client's existing infra"]* |
| Monitoring          | *[e.g., "CloudWatch + Sentry"]* | *[e.g., "Quick setup, good error tracking"]* |
| CI/CD               | *[e.g., "GitHub Actions"]*  | *[e.g., "Team already uses GitHub"]*          |

---

## Dependency Graph

*Which requirements depend on others? What is the build order?*

```
*[Replace with your dependency diagram]*

Example:

[Requirement 3: Search] --depends on--> [Requirement 1: Data Ingestion]
[Requirement 2: Notifications] --depends on--> [Requirement 1: Data Ingestion]
[Requirement 4: Analytics] --depends on--> [Requirement 1: Data Ingestion] + [Requirement 3: Search]
```

### Recommended Build Order

1. *[e.g., "Requirement 1 -- Data ingestion (everything depends on this)"]*
2. *[e.g., "Requirement 3 -- Search (enables dashboard)"]*
3. *[e.g., "Requirement 2 -- Notifications (uses same data pipeline)"]*
4. *[e.g., "Remaining requirements in priority order"]*

---

## Gaps and Open Questions

| #  | Gap / Question                                   | Impact if Unresolved              | Owner      | Due Date   |
|----|--------------------------------------------------|-----------------------------------|------------|------------|
| 1  | *[e.g., "Do we have API docs for carrier X?"]*   | *[e.g., "Cannot build ingestion"]* | *[Name]* | *[Date]*   |
| 2  | *[e.g., "What auth system does the client use?"]* | *[e.g., "Cannot implement SSO"]* | *[Name]*  | *[Date]*   |
| 3  | *[Gap/Question]*                                 | *[Impact]*                        | *[Name]*   | *[Date]*   |
| 4  | *[Gap/Question]*                                 | *[Impact]*                        | *[Name]*   | *[Date]*   |

---

*Review this mapping with your technical lead before starting implementation. Update it as you learn more -- technology choices in a POC should be pragmatic, not perfect.*
