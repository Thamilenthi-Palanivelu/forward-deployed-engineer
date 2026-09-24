# Internal Communication Templates

## Template 1: Engineering Team Update

### Subject

*[Project Name] Engineering Update — Week of [Date]*

### Audience

*Engineering team, Tech Leads, Engineering Manager*

### Key Message

*One sentence summarizing the most important thing the team should know this week.*

*e.g., "We completed the RAG pipeline integration and are now focused on evaluation and performance optimization."*

### Details

**What shipped this week:**
- *Feature/component 1: Brief description of what was completed*
- *Feature/component 2: Brief description of what was completed*
- *Bug fix / improvement: Brief description*

**What's in progress:**
- *Work item 1: Current status, expected completion*
- *Work item 2: Current status, expected completion*

**Blockers / Risks:**
- *Blocker 1: Description, who can help unblock*
- *Risk 1: Description, mitigation plan*

**Technical decisions made:**
- *Decision 1: What was decided and why (link to ADR if applicable)*
- *Decision 2: What was decided and why*

**Key metrics:**
| Metric | This Week | Last Week | Trend |
|--------|-----------|-----------|-------|
| *e.g., AI response accuracy* | *__%* | *__%* | *Up/Down/Flat* |
| *e.g., P95 latency* | *__ ms* | *__ ms* | *Up/Down/Flat* |
| *e.g., Test coverage* | *__%* | *__%* | *Up/Down/Flat* |

### Ask

*What do you need from the team?*

- *e.g., Code review on PR #XXX by Thursday*
- *e.g., Input on [technical decision] — async feedback in [channel/doc]*
- *e.g., Volunteers for on-call rotation starting [date]*

---

## Template 2: Product Team Alignment Request

### Subject

*[Project Name] — Alignment Needed: [Topic]*

### Audience

*Product Manager, Product Designer, relevant stakeholders*

### Key Message

*One sentence framing the alignment needed.*

*e.g., "We've encountered a trade-off between AI response quality and latency that requires a product decision on acceptable thresholds."*

### Details

**Context:**
*Provide enough background for the product team to understand the situation. Keep it non-technical where possible.*

*e.g., "During testing of the AI-powered [feature], we found that higher-quality responses take 3-5 seconds, while faster responses (< 1 second) have lower accuracy. We need to decide which user experience to optimize for."*

**Options:**

| Option | Description | User Impact | Technical Effort | Recommendation |
|--------|-------------|-------------|-----------------|----------------|
| **A** | *Description of option A* | *e.g., Better accuracy, slower UX* | *e.g., Low — current implementation* | *Recommended / Not recommended* |
| **B** | *Description of option B* | *e.g., Faster UX, lower accuracy* | *e.g., Medium — requires caching layer* | *Recommended / Not recommended* |
| **C** | *Description of option C* | *e.g., Hybrid approach with streaming* | *e.g., High — significant rework* | *Recommended / Not recommended* |

**Engineering recommendation:** *State which option you recommend and why, while making it clear this is a product decision.*

**Timeline impact:** *How does each option affect the delivery timeline?*

### Ask

*Be specific about what you need and by when.*

- *Decision needed by: [Date]*
- *Decision maker: [Name/Role]*
- *How to provide input: [Meeting / async in doc / Slack thread]*
- *If no decision by [date], we will proceed with Option [X] as the default*

---

## Template 3: Leadership Status Report

### Subject

*[Project Name] — Status Report: [Month/Sprint]*

### Audience

*VP Engineering, CTO, Director of Product, other senior leadership*

### Key Message

*One sentence executive summary. Lead with the most important insight.*

*e.g., "The AI claims processing pilot reduced manual review time by 40% in Week 2, and we're on track for production deployment by [date]."*

### Details

**Overall Status:** *On Track / At Risk / Behind Schedule / Ahead of Schedule*

**Progress Summary:**

| Milestone | Target Date | Status | Notes |
|-----------|-------------|--------|-------|
| *e.g., Architecture finalized* | *YYYY-MM-DD* | *Complete* | |
| *e.g., RAG pipeline deployed to staging* | *YYYY-MM-DD* | *Complete* | |
| *e.g., Security review passed* | *YYYY-MM-DD* | *In Progress* | *Review scheduled for [date]* |
| *e.g., Pilot launch with 10 users* | *YYYY-MM-DD* | *On Track* | |
| *e.g., Full production rollout* | *YYYY-MM-DD* | *On Track* | |

**Key Achievements This Period:**
- *Achievement 1 with quantified impact where possible*
- *Achievement 2*

**Risks and Mitigations:**

| Risk | Likelihood | Impact | Mitigation | Owner |
|------|-----------|--------|------------|-------|
| *e.g., AI accuracy below target* | *Medium* | *High* | *Additional eval cycles, prompt tuning* | *FDE* |
| *e.g., User adoption resistance* | *Medium* | *Medium* | *Champion program, training sessions* | *PM* |
| | | | | |

**Budget / Cost:**

| Category | Budgeted | Actual | Variance | Notes |
|----------|----------|--------|----------|-------|
| *AI API costs* | *$__/month* | *$__/month* | *+/- $__%* | |
| *Infrastructure* | *$__/month* | *$__/month* | *+/- $__%* | |
| *Total* | *$__/month* | *$__/month* | *+/- $__%* | |

**Customer / User Impact:**
- *e.g., Pilot users processing X% more claims per day*
- *e.g., User satisfaction score: X/5*

### Ask

*What decisions or support do you need from leadership?*

- *e.g., Approval to expand pilot from 10 to 50 users*
- *e.g., Budget increase of $X/month for AI API costs*
- *e.g., Executive sponsor to present at [stakeholder meeting]*
- *e.g., No blockers — FYI only*

**Next update:** *[Date]*
