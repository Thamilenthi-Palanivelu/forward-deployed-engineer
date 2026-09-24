# One-Page Technical Design

> Constraint breeds clarity. This entire design must fit conceptually on one page. If you cannot explain your system this concisely, you do not understand it well enough yet.

---

## Problem

*[Two sentences maximum. State the problem, not the solution.]*

*[e.g., "Customer service representatives cannot access real-time shipment status, forcing them to manually query three separate systems for every customer inquiry. This wastes 75 hours of labor per week and is driving customer attrition."]*

---

## Solution

*[Two sentences maximum. State what the system does, not how it does it.]*

*[e.g., "A unified tracking service that aggregates shipment data from all sources into a single real-time view with sub-second lookup. The system proactively notifies customers of delays before they need to call."]*

---

## Architecture Diagram

```
*[Replace this with your architecture diagram using text/ASCII art]*

Example:

                    +------------------+
                    |   Dashboard UI   |
                    |   (React SPA)    |
                    +--------+---------+
                             |
                             | REST API
                             |
                    +--------+---------+
                    |   API Gateway    |
                    |   (FastAPI)      |
                    +--------+---------+
                             |
              +--------------+--------------+
              |                             |
    +---------+----------+      +-----------+---------+
    |  Tracking Engine   |      |  Notification Svc   |
    |  (Event Processor) |      |  (Email / SMS)      |
    +---------+----------+      +-----------+---------+
              |                             |
    +---------+----------+                  |
    |  Message Queue     +------------------+
    |  (Redis Streams)   |
    +---------+----------+
              |
    +---------+---+--------+----------+
    |             |                    |
+---+---+   +----+-----+   +---------+--+
| WMS   |   | Carrier  |   | Legacy     |
| API   |   | GPS Feed |   | Tracking DB|
+-------+   +----------+   +------------+
```

---

## Key Components

| Component           | Responsibility                              | Technology        | Notes                          |
|---------------------|---------------------------------------------|-------------------|--------------------------------|
| *[e.g., "Ingestion"]* | *[e.g., "Pull data from 3 sources"]*     | *[e.g., "Python workers"]* | *[e.g., "5-min poll for WMS, webhook for GPS"]* |
| *[e.g., "Queue"]*  | *[e.g., "Decouple ingestion from processing"]* | *[e.g., "Redis Streams"]* | *[e.g., "Swap for Kafka in prod if needed"]* |
| *[e.g., "Engine"]*  | *[e.g., "Normalize, dedupe, calculate ETA"]* | *[e.g., "Python"]* | *[e.g., "Stateless; all state in DB"]* |
| *[e.g., "API"]*     | *[e.g., "Serve tracking data to frontend"]* | *[e.g., "FastAPI"]* | *[e.g., "< 200ms p99 target"]*  |
| *[e.g., "UI"]*      | *[e.g., "Display tracking, search, map"]*  | *[e.g., "React"]*  | *[e.g., "Embeds in Zendesk via iframe"]* |
| *[e.g., "Alerts"]*  | *[e.g., "Send delay notifications"]*       | *[e.g., "SES"]*    | *[e.g., "Email only for POC"]*  |

---

## Data Flow

*Describe how data moves through the system, step by step.*

1. *[e.g., "Ingestion workers poll WMS API (every 5 min) and listen to carrier GPS webhooks"]*
2. *[e.g., "Raw events are published to the message queue with source metadata"]*
3. *[e.g., "Tracking engine consumes events, normalizes to unified schema, writes to PostgreSQL"]*
4. *[e.g., "Engine checks delay rules; if triggered, publishes notification event"]*
5. *[e.g., "Notification service sends email via SES"]*
6. *[e.g., "Dashboard queries API; API reads from PostgreSQL; response cached for 30 seconds"]*

---

## Success Metrics

| Metric                              | Target                    | How Measured                        |
|-------------------------------------|---------------------------|-------------------------------------|
| *[e.g., "API response time"]*       | *[e.g., "< 200ms p99"]*  | *[e.g., "Application metrics"]*     |
| *[e.g., "Data freshness"]*          | *[e.g., "< 10 min lag"]* | *[e.g., "Ingestion timestamp vs. source timestamp"]* |
| *[e.g., "Notification delivery"]*   | *[e.g., "< 5 min from event"]* | *[e.g., "Event log comparison"]* |
| *[e.g., "System uptime"]*           | *[e.g., "99% during POC"]* | *[e.g., "Health check monitoring"]* |
| *[Metric]*                          | *[Target]*                | *[Method]*                          |

---

## Open Questions

*List technical unknowns that could change the design.*

| #  | Question                                                    | Impact on Design                    | Plan to Resolve                     |
|----|-------------------------------------------------------------|-------------------------------------|-------------------------------------|
| 1  | *[e.g., "What is the WMS API rate limit?"]*                 | *[e.g., "Determines poll frequency"]* | *[e.g., "Ask client IT by Day 11"]* |
| 2  | *[e.g., "Can we get a webhook from the carrier, or must we poll?"]* | *[e.g., "Affects data freshness"]* | *[e.g., "Test carrier API this week"]* |
| 3  | *[e.g., "Does Zendesk support iframe embedding?"]*          | *[e.g., "Affects UI integration approach"]* | *[e.g., "Check docs today"]* |
| 4  | *[Question]*                                                | *[Impact]*                          | *[Resolution plan]*                 |

---

*If this design cannot fit on one page (conceptually), you are overbuilding for a POC. Simplify.*
