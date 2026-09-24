# Scoping Decision Document

> Scenario: Your customer has requested 5 features for the engagement, but given timeline and resource constraints, you can only deliver 2 in the POC. This document captures your prioritization reasoning and communication plan.

---

## Feature Requests

*List all features the customer has requested, with their stated reasoning.*

| #  | Feature Requested                                  | Customer's Reasoning                           | Requested By       |
|----|----------------------------------------------------|-------------------------------------------------|--------------------|
| 1  | *[e.g., "Real-time tracking dashboard"]*           | *[e.g., "CS reps need instant status access"]* | *[e.g., "VP Ops"]* |
| 2  | *[e.g., "Automated delay notifications"]*          | *[e.g., "Reduce inbound call volume"]*         | *[e.g., "CS Lead"]* |
| 3  | *[e.g., "Predictive ETA engine"]*                  | *[e.g., "Proactive customer communication"]*   | *[e.g., "VP Ops"]* |
| 4  | *[e.g., "Driver mobile app"]*                      | *[e.g., "Eliminate manual checkpoint scans"]*  | *[e.g., "Logistics Mgr"]* |
| 5  | *[e.g., "Analytics and reporting dashboard"]*      | *[e.g., "Monthly performance visibility"]*     | *[e.g., "CEO"]*    |

---

## Prioritization Criteria

*Define the criteria you are using to prioritize. Be transparent -- share these with the customer.*

| Criterion              | Weight | Description                                                     |
|------------------------|--------|-----------------------------------------------------------------|
| Business Impact        | *[e.g., 30%]* | *How directly does this address the core problem?*        |
| Feasibility in POC     | *[e.g., 25%]* | *Can we build this in the POC timeline (2-3 weeks)?*      |
| Data/Integration Readiness | *[e.g., 20%]* | *Are the required data sources and APIs available now?* |
| Stakeholder Alignment  | *[e.g., 15%]* | *Does the decision-maker care about this feature?*        |
| Foundation for Future   | *[e.g., 10%]* | *Does this enable the deferred features later?*          |

---

## Impact/Effort Matrix

*Score each feature and plot it on the matrix.*

| Feature                        | Impact (1-5) | Effort (1-5) | Data Ready? | Stakeholder Priority | Total Score | Quadrant          |
|--------------------------------|--------------|--------------|-------------|----------------------|-------------|-------------------|
| *[Feature 1]*                  | *[Score]*    | *[Score]*    | *[Y/N]*     | *[H/M/L]*           | *[Total]*   | *[Do First / Plan / Quick Win / Defer]* |
| *[Feature 2]*                  | *[Score]*    | *[Score]*    | *[Y/N]*     | *[H/M/L]*           | *[Total]*   | *[Quadrant]*      |
| *[Feature 3]*                  | *[Score]*    | *[Score]*    | *[Y/N]*     | *[H/M/L]*           | *[Total]*   | *[Quadrant]*      |
| *[Feature 4]*                  | *[Score]*    | *[Score]*    | *[Y/N]*     | *[H/M/L]*           | *[Total]*   | *[Quadrant]*      |
| *[Feature 5]*                  | *[Score]*    | *[Score]*    | *[Y/N]*     | *[H/M/L]*           | *[Total]*   | *[Quadrant]*      |

```
        High Impact
             |
   Plan      |   Do First
   (F3, F5)  |   (F1, F2)
             |
 ------------|------------
             |
   Defer     |   Quick Win
   (F4)      |   (none)
             |
        Low Impact

      High Effort    Low Effort
```

*[Adjust the quadrant placement based on your actual scores]*

---

## Recommended POC Scope

### In Scope (POC Features)

**Feature 1: *[Name]***
- Why: *[e.g., "Highest impact, directly addresses the core tracking problem, data sources are ready"]*
- What we will deliver: *[e.g., "A web-based dashboard showing real-time shipment status with location, status, and ETA for all active shipments"]*
- Dependencies: *[e.g., "API access to warehouse system, GPS feed credentials"]*

**Feature 2: *[Name]***
- Why: *[e.g., "Directly reduces CS call volume (the measurable success criterion), builds on Feature 1's data pipeline"]*
- What we will deliver: *[e.g., "Automated email/SMS notifications when a shipment is delayed by more than 1 hour"]*
- Dependencies: *[e.g., "Customer contact data, email/SMS service account"]*

---

## What We're Deferring and Why

*Be honest and specific. Customers respect transparency more than vague promises.*

| Feature Deferred        | Why It's Deferred                                    | When It Could Be Built        | What We Need First              |
|-------------------------|------------------------------------------------------|-------------------------------|---------------------------------|
| *[Feature 3]*           | *[e.g., "Requires ML model training with 6+ months of historical data we don't have yet"]* | *[e.g., "Phase 2, month 2-3"]* | *[e.g., "Data collection during POC"]* |
| *[Feature 4]*           | *[e.g., "Requires mobile development expertise and driver workflow redesign -- separate workstream"]* | *[e.g., "Phase 3, month 4+"]* | *[e.g., "Driver user research"]* |
| *[Feature 5]*           | *[e.g., "Analytics are most valuable once tracking data is flowing reliably -- build on top of POC"]* | *[e.g., "Phase 2, month 2"]* | *[e.g., "2-4 weeks of tracked data"]* |

### How POC Features Enable Deferred Features

*Show the customer that deferring is not abandoning -- it is sequencing.*

- *[e.g., "The data pipeline we build for the tracking dashboard (Feature 1) is the same pipeline that will feed the predictive ETA engine (Feature 3) and analytics dashboard (Feature 5)."]*
- *[e.g., "Delay notification logic (Feature 2) establishes the notification infrastructure that the driver mobile app (Feature 4) will also use."]*

---

## Customer Communication Plan

### Key Messages

1. **We heard you.** All five features matter and we have a plan for all of them.
2. **We are being strategic.** Starting with Features 1 and 2 gives you the fastest path to measurable impact.
3. **We are building a foundation.** The POC features create the infrastructure for everything else.
4. **We are not saying no.** We are saying "not yet" -- and here is when.

### Conversation Script

*Use this as a guide, not a word-for-word script.*

> "Thank you for sharing your vision -- all five of these features would create tremendous value. Here is what I recommend for the POC. Given our [X-week] timeline and the goal of demonstrating clear ROI, I suggest we focus on [Feature 1] and [Feature 2]. Here is why..."
>
> "The great news is that the architecture we build for these two features directly enables [Feature 3] and [Feature 5] in the next phase. Think of the POC as building the engine -- Phases 2 and 3 add the body and the paint."
>
> "Does this sequencing make sense to you? Is there a feature I've deferred that you feel is more urgent than what I've proposed?"

### Handling Pushback

| If the customer says...                  | Respond with...                                           |
|------------------------------------------|-----------------------------------------------------------|
| "We need all five features."             | *[e.g., "I understand the urgency. If we try to build all five in [X weeks], we risk delivering none of them well. Let me show you how Features 1 and 2 get you 70% of the value in 30% of the time."]*  |
| "Can you add just one more?"             | *[e.g., "Which one? Let me look at the effort. If it is [Feature 5], we might be able to include a basic version. Let me re-scope and get back to you by tomorrow."]*  |
| "Our CEO really wants [deferred feature]." | *[e.g., "That is important context. Can we schedule 15 minutes with [CEO] so I can understand their priorities directly? I want to make sure we are optimizing for the right outcome."]*  |

---

*This document should be shared with your internal team before the customer conversation. Get alignment on the recommendation before presenting it.*
