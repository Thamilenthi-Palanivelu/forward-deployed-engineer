# Prioritization Exercise

## Feature / Task Backlog

| # | Feature/Task | Business Impact (1-5) | Technical Effort (1-5) | Risk (1-5) | Priority Score | Recommendation |
|---|-------------|----------------------|----------------------|------------|---------------|----------------|
| 1 | *e.g., RAG pipeline for internal docs* | *5* | *3* | *2* | *__* | *Do first* |
| 2 | *e.g., User authentication and RBAC* | *4* | *2* | *1* | *__* | *Do first* |
| 3 | *e.g., Real-time streaming responses* | *3* | *4* | *3* | *__* | *Do later* |
| 4 | *e.g., Multi-language support* | *2* | *4* | *2* | *__* | *Defer* |
| 5 | *e.g., Custom model fine-tuning* | *3* | *5* | *4* | *__* | *Defer* |
| 6 | *e.g., Analytics dashboard* | *4* | *3* | *1* | *__* | *Do next* |
| 7 | *e.g., Prompt injection guardrails* | *5* | *2* | *2* | *__* | *Do first* |
| 8 | *e.g., Mobile app support* | *2* | *5* | *3* | *__* | *Cut* |
| 9 | | | | | | |
| 10 | | | | | | |
| 11 | | | | | | |
| 12 | | | | | | |

**Scoring Key:**
- **Business Impact** (1-5): 1 = Nice to have, 5 = Critical for success
- **Technical Effort** (1-5): 1 = Trivial (hours), 5 = Major (weeks+)
- **Risk** (1-5): 1 = Well understood, 5 = High uncertainty/many unknowns

**Priority Score Formula:** *Document your formula here*

*Option A (WSJF-inspired):* `Priority = Business Impact / Technical Effort`

*Option B (Weighted):* `Priority = (Business Impact * 3) - (Technical Effort * 1) - (Risk * 1)`

*Option C (ICE):* `Priority = (Impact + Confidence + Ease) / 3`

*Choose one and apply consistently. Write the formula you used:*

> **Formula used:** *___________*

## Methodology Used

### Framework: *[Name the framework you chose]*

*Explain which prioritization framework you used and why it was appropriate for this context.*

**Options considered:**
- **RICE** (Reach, Impact, Confidence, Effort) — *Good when you have usage data and want to maximize reach*
- **WSJF** (Weighted Shortest Job First) — *Good for maximizing value delivered per unit time*
- **MoSCoW** (Must/Should/Could/Won't) — *Good for scope negotiation with stakeholders*
- **ICE** (Impact, Confidence, Ease) — *Good for quick prioritization with limited data*
- **Value vs. Effort Matrix** — *Good for visual communication with non-technical stakeholders*

**Why this framework:** *Explain your choice. e.g., "We chose RICE because we have early usage data from the pilot and need to justify priorities to business stakeholders with quantitative reasoning."*

### Value vs. Effort Matrix

*Plot your features on this matrix for a visual overview.*

```
                        HIGH VALUE
                             │
         ┌───────────────────┼───────────────────┐
         │                   │                   │
         │   BIG BETS        │   QUICK WINS      │
         │   (Invest         │   (Do First)      │
HIGH     │    carefully)     │                   │
EFFORT   │                   │   Items: #__      │
         │   Items: #__      │          #__      │
         │          #__      │                   │
         ├───────────────────┼───────────────────┤
         │                   │                   │
         │   MONEY PIT       │   FILL-INS        │
         │   (Avoid)         │   (Do if time     │
LOW      │                   │    permits)       │
EFFORT   │   Items: #__      │                   │
         │          #__      │   Items: #__      │
         │                   │          #__      │
         └───────────────────┼───────────────────┘
                             │
                        LOW VALUE
```

## Justification for Top 3

### Priority 1: *[Feature/Task Name]*

- **Why this is #1:** *Explain the business and technical reasoning*
- **Expected outcome:** *What will be achieved when this is done?*
- **Dependencies:** *What must be true for this to succeed?*
- **Timeline:** *Estimated duration*
- **Success criteria:** *How will you know it's done well?*

### Priority 2: *[Feature/Task Name]*

- **Why this is #2:** *Explain the business and technical reasoning*
- **Expected outcome:** *What will be achieved when this is done?*
- **Dependencies:** *What must be true for this to succeed?*
- **Timeline:** *Estimated duration*
- **Success criteria:** *How will you know it's done well?*

### Priority 3: *[Feature/Task Name]*

- **Why this is #3:** *Explain the business and technical reasoning*
- **Expected outcome:** *What will be achieved when this is done?*
- **Dependencies:** *What must be true for this to succeed?*
- **Timeline:** *Estimated duration*
- **Success criteria:** *How will you know it's done well?*

## What Gets Cut and Why

### Deferred Items

| Item | Why It's Deferred | What Would Change This Decision | Revisit Date |
|------|------------------|--------------------------------|-------------|
| *e.g., Multi-language support* | *Low user demand in pilot market; high effort* | *Expansion to non-English markets* | *Q3 review* |
| *e.g., Custom fine-tuning* | *Prompt engineering achieving acceptable quality; fine-tuning is high-effort/high-risk* | *Accuracy plateau that can't be solved with prompting* | *After 60-day pilot* |
| *e.g., Mobile app* | *80% of users access via desktop; mobile ROI unclear* | *Usage data showing significant mobile demand* | *Next quarter* |
| | | | |

### How to Communicate "No" (or "Not Yet")

*For each deferred item, prepare a one-sentence explanation for stakeholders:*

- **To [stakeholder] about [deferred item]:** *"We're prioritizing [top priority] first because [reason]. We'll revisit [deferred item] in [timeframe] once we have [data/milestone]."*
- **To [stakeholder] about [deferred item]:** *"..."*
- **To [stakeholder] about [deferred item]:** *"..."*

## Notes and Reflections

*After completing this exercise, reflect on:*

- *What made prioritization difficult?*
- *Where did you and stakeholders disagree? How was it resolved?*
- *What data would have made this exercise easier?*
- *What would you change about the process next time?*
