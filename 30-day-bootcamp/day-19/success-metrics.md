# KPI Tracking Template

## KPI Dashboard

| # | KPI | Baseline | Target | Current | Trend | Status |
|---|-----|----------|--------|---------|-------|--------|
| 1 | *e.g., AI response accuracy* | *72%* | *> 90%* | *__%* | *Up / Down / Flat* | *On Track / At Risk / Behind* |
| 2 | *e.g., Average response latency (P95)* | *5.2s* | *< 2s* | *__ s* | *Up / Down / Flat* | *On Track / At Risk / Behind* |
| 3 | *e.g., User adoption rate* | *0%* | *> 60% of target users* | *__%* | *Up / Down / Flat* | *On Track / At Risk / Behind* |
| 4 | *e.g., Time saved per task* | *15 min/task* | *< 5 min/task* | *__ min* | *Up / Down / Flat* | *On Track / At Risk / Behind* |
| 5 | *e.g., User satisfaction (CSAT)* | *N/A* | *> 4.0/5.0* | *__/5.0* | *Up / Down / Flat* | *On Track / At Risk / Behind* |
| 6 | *e.g., Cost per AI query* | *$0.12* | *< $0.05* | *$__* | *Up / Down / Flat* | *On Track / At Risk / Behind* |
| 7 | *e.g., Hallucination rate* | *15%* | *< 5%* | *__%* | *Up / Down / Flat* | *On Track / At Risk / Behind* |
| 8 | *e.g., System uptime* | *N/A* | *> 99.5%* | *__%* | *Up / Down / Flat* | *On Track / At Risk / Behind* |
| 9 | *e.g., Tasks completed with AI assistance* | *0/day* | *> X/day* | *__/day* | *Up / Down / Flat* | *On Track / At Risk / Behind* |
| 10 | *e.g., Manual escalation rate* | *100%* | *< 30%* | *__%* | *Up / Down / Flat* | *On Track / At Risk / Behind* |
| 11 | | | | | | |
| 12 | | | | | | |

**Status Key:**
- **On Track** = Current trajectory will meet or exceed target
- **At Risk** = Current trajectory may miss target without intervention
- **Behind** = Current value is significantly below target, action required

## Measurement Methodology

### How Each KPI Is Measured

| KPI | Data Source | Measurement Method | Calculation | Frequency |
|-----|-----------|-------------------|-------------|-----------|
| *AI response accuracy* | *Eval pipeline + user feedback* | *Automated eval on sample of responses; user thumbs up/down* | *(Correct responses / Total evaluated) * 100* | *Daily (automated), Weekly (human review)* |
| *Response latency* | *APM / application logs* | *Measure time from request to complete response* | *P95 of all AI request durations* | *Continuous (real-time dashboard)* |
| *User adoption rate* | *Usage analytics* | *Unique active users / Total eligible users* | *(DAU or WAU / Total users with access) * 100* | *Weekly* |
| *Time saved per task* | *Before/after time study* | *Measure task completion time with and without AI* | *Average(manual time) - Average(AI-assisted time)* | *Bi-weekly (sampling)* |
| *User satisfaction* | *In-app survey* | *Post-interaction survey (optional)* | *Average of all survey responses (1-5 scale)* | *Rolling weekly average* |
| *Cost per query* | *AI provider billing + infrastructure costs* | *Total AI spend / Total queries* | *(API costs + infra costs) / Query count* | *Daily* |
| *Hallucination rate* | *Eval pipeline + user reports* | *Automated fact-checking against source docs* | *(Responses with unsupported claims / Total) * 100* | *Daily (automated)* |
| | | | | |

### Data Collection Notes

- *Describe any limitations in data collection*
- *e.g., User satisfaction is opt-in, so may have response bias*
- *e.g., Accuracy eval uses a sample of 100 queries/day, not all queries*
- *e.g., Time saved estimates are based on self-reported data from pilot users*

### Baseline Establishment

*How were baselines determined?*

| KPI | Baseline Method | Baseline Period | Confidence |
|-----|----------------|-----------------|------------|
| *AI accuracy* | *Manual evaluation of first 200 queries* | *Week 1 of pilot* | *Medium — small sample* |
| *Task time* | *Time study with 10 users over 1 week* | *Pre-deployment* | *Medium — limited participants* |
| *Cost per query* | *First month of production usage* | *Month 1* | *High — actual billing data* |
| | | | |

## Reporting Cadence

| Report | Audience | Frequency | Format | Owner | Distribution |
|--------|----------|-----------|--------|-------|-------------|
| **Daily dashboard** | *Engineering + PM* | *Daily (automated)* | *Dashboard link* | *Automated* | *Slack #metrics* |
| **Weekly summary** | *Team + stakeholders* | *Weekly (Monday)* | *Written summary + charts* | *FDE* | *Email + Slack* |
| **Bi-weekly deep dive** | *PM + Engineering Lead* | *Bi-weekly* | *Meeting with deck* | *FDE* | *Calendar invite* |
| **Monthly executive report** | *Leadership* | *Monthly* | *1-page summary* | *PM + FDE* | *Email* |
| **Quarterly business review** | *Executive team* | *Quarterly* | *Presentation* | *PM* | *Meeting* |

### Weekly Report Template

```
Week of [Date]

HEADLINE: [One sentence — the most important thing to know]

KPIs:
  Accuracy:     [current] (target: [target]) [status emoji: checkmark/warning/x]
  Adoption:     [current] (target: [target]) [status emoji]
  Latency P95:  [current] (target: [target]) [status emoji]
  Cost/query:   [current] (target: [target]) [status emoji]

HIGHLIGHTS:
  - [Achievement 1]
  - [Achievement 2]

CONCERNS:
  - [Issue 1 — action being taken]

NEXT WEEK:
  - [Priority 1]
  - [Priority 2]
```

## Escalation Criteria

### When to Escalate

| Condition | Escalate To | Action |
|-----------|-----------|--------|
| *Any KPI moves from "On Track" to "At Risk"* | *PM + Engineering Lead* | *Review in next weekly sync, create action plan* |
| *Any KPI moves from "At Risk" to "Behind"* | *PM + Engineering Lead + Stakeholders* | *Emergency review within 48 hours, adjust plan* |
| *Accuracy drops below X% for 3 consecutive days* | *Engineering Lead* | *Investigate root cause, consider pausing AI features* |
| *Cost exceeds monthly budget by > 20%* | *PM + Finance* | *Cost optimization review, consider rate limiting* |
| *Adoption stalls at < X% for 2 consecutive weeks* | *PM + Change Management* | *User research, adjust rollout strategy* |
| *User satisfaction drops below 3.0/5.0* | *PM + Engineering Lead* | *User interviews, prioritize top complaints* |

### Escalation Process

1. **Identify:** KPI breaches threshold or shows concerning trend
2. **Analyze:** Determine root cause (is it data quality, system issue, or real regression?)
3. **Communicate:** Notify appropriate stakeholders with data and preliminary analysis
4. **Plan:** Create action plan with owner and timeline
5. **Execute:** Implement fixes
6. **Verify:** Confirm KPI returns to acceptable range
7. **Document:** Record what happened and preventive measures

## Historical Tracking

*Use this table to track KPI values over time. Update weekly.*

### Week-over-Week Tracking

| KPI | Week 1 | Week 2 | Week 3 | Week 4 | Week 5 | Week 6 | Week 7 | Week 8 |
|-----|--------|--------|--------|--------|--------|--------|--------|--------|
| *Accuracy* | | | | | | | | |
| *Latency* | | | | | | | | |
| *Adoption* | | | | | | | | |
| *Satisfaction* | | | | | | | | |
| *Cost/query* | | | | | | | | |
| *Hallucination rate* | | | | | | | | |
