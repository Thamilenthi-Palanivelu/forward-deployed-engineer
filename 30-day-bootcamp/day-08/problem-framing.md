# Problem Framing Document

> A well-framed problem is half-solved. Use this document to sharpen your thinking before jumping to solutions. Share it with stakeholders to confirm alignment.

---

## Problem Statement

*Write the problem in one clear sentence. It should be specific, measurable, and free of solution language.*

> *[e.g., "Customer service representatives spend an average of 3 hours per day manually looking up shipment statuses across multiple systems, resulting in slow response times and a 40% drop in customer satisfaction scores."]*

### Validation Checklist

- [ ] The statement describes a *problem*, not a solution
- [ ] It includes who is affected
- [ ] It includes a measurable impact
- [ ] A non-technical stakeholder can understand it
- [ ] The client agrees this is the problem

---

## Business Impact

*Quantify the cost of this problem. Use the client's own numbers where possible.*

| Impact Category        | Metric                                       | Value                    |
|------------------------|-----------------------------------------------|--------------------------|
| Revenue at Risk        | *[e.g., "Largest customer threatening to leave"]* | *[e.g., "$18M/year"]*  |
| Operational Cost       | *[e.g., "Hours spent on manual tracking"]*    | *[e.g., "15 hrs/day across team"]* |
| Customer Satisfaction  | *[e.g., "NPS score decline"]*                 | *[e.g., "58 to 32 over 18 months"]* |
| Employee Impact        | *[e.g., "Agent burnout and turnover"]*        | *[e.g., "35% annual turnover"]* |
| Opportunity Cost       | *[e.g., "Cannot onboard new enterprise clients"]* | *[e.g., "$5M pipeline stalled"]* |

**Total Estimated Annual Cost of the Problem:** *[$X]*

---

## Current Workarounds

*How are people dealing with this problem today? Workarounds reveal both the severity and the implicit requirements.*

| #  | Workaround                                         | Who Does It        | Time Spent     | Limitations                     |
|----|----------------------------------------------------|--------------------|----------------|---------------------------------|
| 1  | *[e.g., "Call warehouse directly for status"]*     | *[CS reps]*        | *[1 hr/day]*   | *[Not scalable, unreliable]*    |
| 2  | *[e.g., "Export spreadsheet from legacy system"]*  | *[Ops manager]*    | *[30 min/day]* | *[Data is stale by export time]* |
| 3  | *[Workaround 3]*                                   | *[Who]*            | *[Time]*       | *[Limitations]*                 |

---

## Constraints

*What boundaries must the solution work within?*

### Technical Constraints

- *[e.g., "Must integrate with existing SAP system -- cannot replace it"]*
- *[e.g., "Data must remain in US-based data centers (compliance)"]*
- *[e.g., "Legacy API supports only SOAP, no REST"]*

### Business Constraints

- *[e.g., "Budget capped at $200K for initial phase"]*
- *[e.g., "Must show results before Q4 board meeting"]*
- *[e.g., "Cannot disrupt operations during peak season (Nov-Dec)"]*

### Organizational Constraints

- *[e.g., "Only 2 developers available on client side"]*
- *[e.g., "VP of Engineering must approve any cloud deployments"]*
- *[e.g., "Union rules limit changes to warehouse floor processes"]*

---

## Success Criteria

*How will we know the problem is solved? Define measurable criteria the client agrees to.*

| #  | Success Criterion                                    | Current Baseline   | Target           | Measurement Method          |
|----|------------------------------------------------------|--------------------|------------------|-----------------------------|
| 1  | *[e.g., "Time to answer shipment status query"]*     | *[e.g., "15 min"]* | *[e.g., "< 30 sec"]* | *[e.g., "Avg response time in CS tool"]* |
| 2  | *[e.g., "Customer satisfaction score"]*              | *[Baseline]*       | *[Target]*       | *[Method]*                  |
| 3  | *[e.g., "Manual hours spent on tracking per week"]*  | *[Baseline]*       | *[Target]*       | *[Method]*                  |
| 4  | *[Criterion 4]*                                      | *[Baseline]*       | *[Target]*       | *[Method]*                  |

### Must-Have vs. Nice-to-Have

- **Must-Have:** *[List criteria that are non-negotiable for the POC to be considered successful]*
- **Nice-to-Have:** *[List criteria that would be great but are not deal-breakers]*

---

## Proposed Approach

*At a high level, how do you intend to solve this? Keep it brief -- the solution brief (Day 9) will go deeper.*

### Approach Summary

*[2-3 sentences describing the proposed approach]*

### Why This Approach

*[Why is this the right approach given the constraints and success criteria? What alternatives did you consider and reject?]*

### Key Assumptions

*List assumptions that must hold true for this approach to work.*

1. *[e.g., "The client can provide API access to their warehouse management system"]*
2. *[e.g., "GPS data from carrier partners is available in near-real-time"]*
3. *[e.g., "The client team can dedicate 5 hours/week to testing during the POC"]*

---

## Out of Scope

*Explicitly state what this engagement will NOT address. This prevents scope creep and sets clear expectations.*

| Item                                          | Reason for Exclusion                          |
|-----------------------------------------------|-----------------------------------------------|
| *[e.g., "Warehouse management system replacement"]* | *[e.g., "Separate initiative, different budget"]* |
| *[e.g., "International shipment tracking"]*   | *[e.g., "Adds regulatory complexity; Phase 2"]* |
| *[e.g., "Mobile app for drivers"]*            | *[e.g., "Requires 3+ months; POC focuses on customer-facing tracking"]* |
| *[Item 4]*                                    | *[Reason]*                                    |

---

## Sign-Off

| Role                  | Name       | Date       | Agreement |
|-----------------------|------------|------------|-----------|
| Client Sponsor        | *[Name]*   | *[Date]*   | [ ]       |
| Technical Lead        | *[Name]*   | *[Date]*   | [ ]       |
| FDE Lead              | *[Name]*   | *[Date]*   | [ ]       |

---

*A signed problem framing document prevents the single most common FDE failure: solving the wrong problem.*
