# POC Scope Document

> A POC is not a product. It is a hypothesis test. This document defines what you are testing, how you will know if it works, and when to stop.

---

## Hypothesis

*State the hypothesis you are testing in one clear sentence. A good POC hypothesis is falsifiable.*

> *[e.g., "If we provide customer service representatives with a unified real-time shipment tracking dashboard, we can reduce average status lookup time from 15 minutes to under 30 seconds and decrease tracking-related call volume by at least 40%."]*

### Hypothesis Validation Checklist

- [ ] The hypothesis is specific and measurable
- [ ] We can test it within the POC timeline
- [ ] The client agrees this is the right thing to test
- [ ] Success or failure will be unambiguous

---

## Success Criteria

*Define exactly what "success" means. Get the client to agree to these before building.*

| #  | Criterion                                     | Metric                   | Target                    | Must-Have or Nice-to-Have |
|----|-----------------------------------------------|--------------------------|---------------------------|---------------------------|
| 1  | *[e.g., "Lookup speed"]*                      | *[Avg time to answer]*   | *[e.g., "< 30 seconds"]* | *[Must-Have]*             |
| 2  | *[e.g., "Data accuracy"]*                     | *[% records correct]*    | *[e.g., "> 95%"]*        | *[Must-Have]*             |
| 3  | *[e.g., "User satisfaction"]*                 | *[Rep feedback score]*   | *[e.g., "4+/5"]*         | *[Must-Have]*             |
| 4  | *[e.g., "Notification delivery"]*             | *[Delivery time]*        | *[e.g., "< 5 min"]*      | *[Nice-to-Have]*          |
| 5  | *[Criterion]*                                 | *[Metric]*               | *[Target]*                | *[Must/Nice]*             |

---

## In Scope / Out of Scope

| Category        | In Scope                                              | Out of Scope                                        |
|-----------------|-------------------------------------------------------|-----------------------------------------------------|
| Features        | *[e.g., "Real-time tracking dashboard, delay notifications"]* | *[e.g., "Predictive ETA, analytics, mobile app"]* |
| Data Sources    | *[e.g., "WMS API, Carrier X GPS feed"]*               | *[e.g., "Carrier Y, Z (different API formats)"]*   |
| Users           | *[e.g., "3-5 CS reps in pilot group"]*                | *[e.g., "All CS reps, end customers"]*              |
| Geography       | *[e.g., "US domestic shipments only"]*                | *[e.g., "International routes"]*                    |
| Scale           | *[e.g., "Up to 5,000 active shipments"]*              | *[e.g., "Full production load (50K+)"]*             |
| Security        | *[e.g., "Basic auth, HTTPS"]*                         | *[e.g., "SSO integration, audit logging"]*          |
| Infrastructure  | *[e.g., "Single-region deployment"]*                  | *[e.g., "Multi-region, HA, DR"]*                    |

---

## Technical Architecture

*Keep it minimal. A POC architecture should be the simplest thing that can validate the hypothesis.*

```
*[Your architecture diagram here]*
```

### Technology Choices

| Component        | Technology           | Why This Choice for POC                            |
|------------------|----------------------|----------------------------------------------------|
| *[e.g., "API"]*  | *[e.g., "FastAPI"]*  | *[e.g., "Fast to build, async support, auto-docs"]* |
| *[e.g., "DB"]*   | *[e.g., "SQLite"]*   | *[e.g., "Zero setup, sufficient for POC volume"]*  |
| *[e.g., "UI"]*   | *[e.g., "React"]*    | *[e.g., "Client team knows React"]*                |
| *[Component]*    | *[Technology]*       | *[Rationale]*                                      |

### What We Are Deliberately NOT Building for the POC

- *[e.g., "No automated testing -- manual QA is sufficient for 3-week POC"]*
- *[e.g., "No CI/CD pipeline -- deploying manually from local"]*
- *[e.g., "No error recovery -- if ingestion fails, we restart manually"]*
- *[e.g., "No auth beyond basic API key -- security comes in production"]*

---

## Timeline (5-Day Breakdown)

| Day   | Focus                        | Deliverable                                    | Demo-able? |
|-------|------------------------------|------------------------------------------------|------------|
| Day 1 | *[e.g., "Environment setup, API access, data exploration"]* | *[e.g., "Working dev environment, first API call successful"]* | No |
| Day 2 | *[e.g., "Data ingestion pipeline"]*  | *[e.g., "Live data flowing into local DB"]*  | Maybe      |
| Day 3 | *[e.g., "Core API and basic UI"]*    | *[e.g., "Search by tracking number works"]* | Yes        |
| Day 4 | *[e.g., "Dashboard polish, notifications"]* | *[e.g., "Full tracking view, email alerts working"]* | Yes |
| Day 5 | *[e.g., "Testing, bug fixes, demo prep"]* | *[e.g., "Demo-ready POC"]*                 | Yes        |

### Daily Check-In Format

*At the end of each day, answer these three questions:*

1. What did I accomplish today?
2. What am I doing tomorrow?
3. Am I still on track for the Day 5 demo? If not, what do I cut?

---

## Kill Criteria

*Define the conditions under which you would stop the POC early. This is not failure -- it is intelligence.*

| #  | Kill Criterion                                          | How We Would Know                         | What We Would Do Instead                |
|----|---------------------------------------------------------|-------------------------------------------|-----------------------------------------|
| 1  | *[e.g., "Data quality is too poor to be useful"]*       | *[e.g., "> 30% of records are stale or incorrect"]* | *[e.g., "Pivot to data quality assessment engagement"]* |
| 2  | *[e.g., "API access is blocked by IT policy"]*          | *[e.g., "No credentials after Day 2"]*    | *[e.g., "Use synthetic data; escalate to sponsor"]* |
| 3  | *[e.g., "Client team is unresponsive"]*                 | *[e.g., "No feedback for 3+ business days"]* | *[e.g., "Escalate; reassess engagement viability"]* |
| 4  | *[e.g., "Hypothesis is clearly wrong"]*                 | *[e.g., "The real problem is not tracking but [X]"]* | *[e.g., "Document findings; re-scope engagement"]* |

### When to Push Through vs. When to Stop

- **Push through** when the problem is technical and solvable (slow API, messy data format, UI bug)
- **Stop and re-evaluate** when the problem is fundamental (wrong hypothesis, no stakeholder engagement, impossible constraints)

---

## Resources Needed

### From Your Team

| Resource                    | Who                   | Hours/Week      |
|-----------------------------|-----------------------|-----------------|
| *[e.g., "FDE (you)"]*      | *[Your name]*         | *[e.g., "40"]*  |
| *[e.g., "Technical advisor"]* | *[Name]*            | *[e.g., "5"]*   |
| *[e.g., "Design support"]*  | *[Name]*             | *[e.g., "3"]*   |

### From the Client

| Resource                    | Who                   | Hours/Week      |
|-----------------------------|-----------------------|-----------------|
| *[e.g., "Technical POC"]*  | *[Client contact]*    | *[e.g., "5"]*   |
| *[e.g., "CS reps for pilot"]* | *[Names]*          | *[e.g., "2"]*   |
| *[e.g., "Executive sponsor"]* | *[Name]*           | *[e.g., "1"]*   |

### Infrastructure / Access

- [ ] *[e.g., "AWS account or access to client's cloud environment"]*
- [ ] *[e.g., "API credentials for WMS"]*
- [ ] *[e.g., "API credentials for carrier GPS feed"]*
- [ ] *[e.g., "Sample customer data (anonymized)"]*
- [ ] *[e.g., "Slack channel or communication tool access"]*

---

## Sign-Off

| Role                  | Name       | Date       | Approved |
|-----------------------|------------|------------|----------|
| FDE Lead              | *[Name]*   | *[Date]*   | [ ]      |
| Client Sponsor        | *[Name]*   | *[Date]*   | [ ]      |
| Technical Lead        | *[Name]*   | *[Date]*   | [ ]      |

---

*A good POC scope document saves you from the two most common POC failures: building too much and testing the wrong thing.*
