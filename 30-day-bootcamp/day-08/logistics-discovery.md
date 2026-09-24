# Logistics Company Discovery Notes

> Scenario: SwiftHaul Logistics is a mid-size logistics company (500 employees, $120M revenue) struggling with shipment tracking visibility and rising customer complaints. They have approached your team to explore how technology can help.

---

## Company Background

| Field            | Details                                |
|------------------|----------------------------------------|
| Company          | *SwiftHaul Logistics*                  |
| Industry         | *Freight and Logistics*                |
| Size             | *500 employees, 3 regional warehouses* |
| Revenue          | *$120M annually*                       |
| Key Challenge    | *Shipment tracking and customer satisfaction* |
| Current NPS      | *32 (down from 58 two years ago)*      |

### Context

*SwiftHaul handles 2,000+ shipments daily across the continental US. Their tracking system was built in-house 8 years ago and relies on manual updates from warehouse staff and drivers. Customer complaints about "where is my shipment?" have tripled in the last 18 months. Their largest customer (15% of revenue) has threatened to leave.*

---

## Discovery Conversation Script

Use this five-level questioning approach to go from surface symptoms to root causes.

### Level 1: Open and Broad

*Start wide. Understand the landscape before diving in.*

- "Tell me about your business and how shipment tracking fits into your operations."
- "What prompted you to reach out to us now?"
- "What does a great day look like for your operations team? What does a bad day look like?"

*[Record responses here]*

### Level 2: Process Understanding

*Map the current workflow. Ask them to walk you through it step by step.*

- "Walk me through what happens from the moment a shipment is picked up to when the customer receives it."
- "At each stage, how is tracking information updated? By whom?"
- "How does a customer check on their shipment status today?"
- "What happens when a shipment is delayed? Who finds out first?"

*[Record responses here]*

### Level 3: Pain Point Exploration

*Quantify the pain. Numbers make problems real.*

- "You mentioned customer complaints have tripled -- can you walk me through a specific recent example?"
- "How many hours per week does your team spend responding to 'where is my shipment?' inquiries?"
- "What is the average time between a shipment status change and when it shows up in your system?"
- "Have you lost any customers specifically due to tracking issues?"

*[Record responses here]*

### Level 4: Prior Attempts and Constraints

*Understand what has been tried before and what walls exist.*

- "Have you tried to solve this before? What happened?"
- "Are there any systems or vendors you are locked into?"
- "What is your appetite for change -- are you looking for incremental improvement or a complete overhaul?"
- "What is your budget range for a solution like this?"
- "Are there compliance or regulatory requirements around shipment data?"

*[Record responses here]*

### Level 5: Vision and Success

*Align on what 'done' looks like.*

- "If we could wave a magic wand, what would shipment tracking look like in 12 months?"
- "How would you measure whether this project was successful?"
- "Who in your organization needs to be convinced this is working?"
- "What would make you say 'this was the best investment we made this year'?"

*[Record responses here]*

---

## Key Pain Points Identified

*After the conversation, distill the top pain points.*

| #  | Pain Point                                    | Severity  | Frequency    | Who It Affects       |
|----|-----------------------------------------------|-----------|--------------|----------------------|
| 1  | *[e.g., Tracking updates are 4-6 hours delayed]* | *[High/Med/Low]* | *[Daily/Weekly]* | *[Ops, Customers]* |
| 2  | *[e.g., Customer service reps lack real-time info]* | *[Severity]* | *[Frequency]* | *[Affected group]* |
| 3  | *[e.g., No proactive delay notifications]*    | *[Severity]* | *[Frequency]* | *[Affected group]*   |
| 4  | *[e.g., Manual data entry at each checkpoint]* | *[Severity]* | *[Frequency]* | *[Affected group]*  |
| 5  | *[e.g., No single source of truth for shipment data]* | *[Severity]* | *[Frequency]* | *[Affected group]* |

---

## Root Cause Analysis (Five Whys)

*Pick the most critical pain point and drill down.*

**Starting Problem:** *[e.g., "Customers do not know where their shipments are"]*

| Why #  | Question                                              | Answer                                             |
|--------|-------------------------------------------------------|----------------------------------------------------|
| Why 1  | Why don't customers know where their shipments are?   | *[e.g., "The tracking portal shows stale data"]*   |
| Why 2  | Why does the tracking portal show stale data?         | *[e.g., "Updates depend on manual warehouse scans"]* |
| Why 3  | Why do updates depend on manual scans?                | *[e.g., "The system has no automated GPS/IoT integration"]* |
| Why 4  | Why is there no automated integration?                | *[e.g., "The legacy system cannot ingest real-time feeds"]* |
| Why 5  | Why hasn't the legacy system been upgraded?            | *[e.g., "No budget was allocated; it was 'good enough' until volume grew"]* |

**Root Cause:** *[e.g., "A legacy system that was adequate at lower volumes cannot scale, and there has been no investment in modernization because tracking was not seen as a revenue driver until key customers began leaving."]*

---

## Opportunity Assessment

*Based on your discovery, assess the opportunities.*

| Opportunity                              | Business Value    | Feasibility | Time to Value | Recommendation         |
|------------------------------------------|-------------------|-------------|---------------|------------------------|
| *[e.g., Real-time GPS tracking integration]* | *[High/Med/Low]* | *[H/M/L]*  | *[Weeks/Months]* | *[POC / Phase 1 / Defer]* |
| *[e.g., Automated delay notifications]*  | *[Value]*         | *[Feasibility]* | *[Timeline]* | *[Recommendation]*     |
| *[e.g., Customer self-service portal]*   | *[Value]*         | *[Feasibility]* | *[Timeline]* | *[Recommendation]*     |
| *[e.g., Predictive ETA engine]*          | *[Value]*         | *[Feasibility]* | *[Timeline]* | *[Recommendation]*     |

### Quick Wins

*What can be done in the first 2 weeks to show value?*

1. *[e.g., "Set up automated email alerts when shipments hit key checkpoints"]*
2. *[Quick win 2]*

### Longer-Term Plays

*What requires a larger investment but delivers significant value?*

1. *[e.g., "Build a real-time tracking dashboard with GPS integration"]*
2. *[Longer-term item 2]*

---

*Use this completed document to inform your solution brief (Day 9) and POC scope (Day 11).*
