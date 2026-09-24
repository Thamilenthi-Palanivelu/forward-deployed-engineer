# Monitoring Dashboard Specification

## Key Metrics

### Infrastructure Metrics

| Metric | Target | Alert Threshold | Dashboard Widget | Owner |
|--------|--------|----------------|-----------------|-------|
| CPU utilization | *< 70% average* | *> 85% for 5 min* | *Time series line chart* | *SRE / Platform* |
| Memory utilization | *< 80% average* | *> 90% for 5 min* | *Time series line chart* | *SRE / Platform* |
| Disk usage | *< 75%* | *> 85%* | *Gauge* | *SRE / Platform* |
| Network I/O | *Baseline +/- 2 std dev* | *> 3 std dev from baseline* | *Time series area chart* | *SRE / Platform* |
| Container restarts | *0* | *> 2 in 10 min* | *Counter / event timeline* | *SRE / Platform* |
| | | | | |

### Application Metrics

| Metric | Target | Alert Threshold | Dashboard Widget | Owner |
|--------|--------|----------------|-----------------|-------|
| Request latency (P50) | *< __ ms* | *> __ ms for 5 min* | *Time series with percentile bands* | *Engineering* |
| Request latency (P95) | *< __ ms* | *> __ ms for 5 min* | *Time series with percentile bands* | *Engineering* |
| Request latency (P99) | *< __ ms* | *> __ ms for 5 min* | *Time series with percentile bands* | *Engineering* |
| Error rate (5xx) | *< 0.1%* | *> 1% for 5 min* | *Time series + single stat* | *Engineering* |
| Error rate (4xx) | *< 5%* | *> 10% for 5 min* | *Time series + single stat* | *Engineering* |
| Throughput (req/sec) | *Baseline* | *< 50% of baseline* | *Time series line chart* | *Engineering* |
| Active connections | *< __ concurrent* | *> __ concurrent* | *Gauge* | *Engineering* |
| | | | | |

### Business Metrics

| Metric | Target | Alert Threshold | Dashboard Widget | Owner |
|--------|--------|----------------|-----------------|-------|
| Active users (DAU) | *Trending up* | *> 20% drop day-over-day* | *Time series + comparison* | *Product* |
| Feature adoption rate | *> __%* | *< __ % after launch* | *Funnel chart* | *Product* |
| Task completion rate | *> __%* | *< __%* | *Single stat + trend* | *Product* |
| | | | | |

## AI-Specific Metrics

| Metric | Target | Alert Threshold | Dashboard Widget | How to Measure |
|--------|--------|----------------|-----------------|----------------|
| **AI response latency** | *P95 < __ s* | *P95 > __ s for 5 min* | *Time series with percentile bands* | *Measure time from request to complete response* |
| **Hallucination rate** | *< 5%* | *> 10% over 1 hour* | *Time series + single stat* | *Automated eval on sample of responses, human review flagging* |
| **Retrieval relevance** (RAG) | *> 80% relevant* | *< 60% over 1 hour* | *Time series line chart* | *Cosine similarity scores, re-ranker confidence* |
| **Token usage per request** | *< __ tokens avg* | *> __ tokens avg over 1 hour* | *Histogram + time series* | *Log input/output token counts per request* |
| **Cost per query** | *< $__* | *> $__ avg over 1 hour* | *Time series + cumulative* | *Token count * price per token + retrieval costs* |
| **Daily AI spend** | *< $__/day* | *> $__/day* | *Cumulative line chart + budget bar* | *Aggregate all AI API costs* |
| **Monthly AI spend** | *< $__/month* | *Projected > $__/month* | *Gauge with projection* | *Running monthly total + forecast* |
| **Model error rate** | *< 1%* | *> 5% over 15 min* | *Time series* | *Count of API errors, timeouts, rate limits* |
| **Guardrail trigger rate** | *Baseline* | *> 2x baseline* | *Time series + event log* | *Count of content filter / safety check triggers* |
| **User satisfaction** (thumbs up/down) | *> 80% positive* | *< 60% positive over 24h* | *Pie chart + trend* | *In-app feedback mechanism* |
| | | | | |

## Alerting Rules

### Severity Levels

| Severity | Response Time | Examples | Notification Channel |
|----------|--------------|---------|---------------------|
| **P0 - Critical** | *Immediate (< 5 min)* | *System down, data loss, security breach* | *PagerDuty + phone call* |
| **P1 - High** | *< 30 min* | *Degraded performance, elevated error rate, AI quality drop* | *PagerDuty + Slack #incidents* |
| **P2 - Medium** | *< 4 hours* | *Non-critical feature broken, elevated latency* | *Slack #alerts* |
| **P3 - Low** | *Next business day* | *Minor UI issue, non-blocking bug, cost trending up* | *Slack #alerts (no page)* |

### Alert Definitions

| Alert Name | Condition | Severity | Runbook Link |
|-----------|-----------|----------|-------------|
| *High Error Rate* | *5xx rate > 1% for 5 min* | *P1* | *link to runbook* |
| *AI Latency Spike* | *AI P95 latency > X sec for 5 min* | *P1* | *link to runbook* |
| *AI Cost Spike* | *Daily spend > $X* | *P2* | *link to runbook* |
| *Hallucination Rate Elevated* | *Hallucination > 10% for 1 hour* | *P2* | *link to runbook* |
| *Database Connection Pool Exhausted* | *Available connections < 5* | *P0* | *link to runbook* |
| *Disk Space Critical* | *Disk usage > 90%* | *P1* | *link to runbook* |
| *Model API Rate Limited* | *> 5 rate limit errors in 5 min* | *P2* | *link to runbook* |
| | | | |

### Alert Anti-Patterns to Avoid

- *Alerting on metrics that are not actionable*
- *Alert thresholds that fire too frequently (alert fatigue)*
- *Missing context in alert messages (include links to dashboards and runbooks)*
- *No clear owner for each alert*

## Escalation Procedures

### Escalation Path

```
┌─────────────┐     ┌──────────────┐     ┌──────────────┐     ┌──────────────┐
│  On-Call     │────▶│  Tech Lead   │────▶│  Engineering │────▶│  VP Eng /    │
│  Engineer   │     │              │     │  Manager     │     │  CTO         │
│  (5 min)    │     │  (30 min)    │     │  (1 hour)    │     │  (2 hours)   │
└─────────────┘     └──────────────┘     └──────────────┘     └──────────────┘
```

### Escalation Criteria

| Trigger | Escalation Action |
|---------|-------------------|
| *Alert not acknowledged in 15 min* | *Auto-escalate to Tech Lead* |
| *Incident not resolved in 1 hour* | *Escalate to Engineering Manager* |
| *Customer-facing outage > 30 min* | *Notify VP Engineering* |
| *Data breach suspected* | *Immediately notify Security + Legal + CTO* |
| *AI producing harmful content* | *Immediately disable AI features, notify Tech Lead* |

### Incident Response Template

- **Incident declared:** *Timestamp*
- **Severity:** *P0/P1/P2/P3*
- **Impact:** *What is affected and how many users*
- **Status:** *Investigating / Identified / Monitoring / Resolved*
- **Timeline:** *Key actions taken and when*
- **Root cause:** *To be filled after resolution*
- **Action items:** *Preventive measures*

## Dashboard Layout

*Describe or sketch the dashboard layout.*

### Dashboard 1: Operations Overview

```
┌─────────────────────────────────────────────┐
│  [Uptime %]  [Error Rate]  [Avg Latency]   │  ← Single stat row
├──────────────────────┬──────────────────────┤
│  Request Rate        │  Error Rate          │  ← Time series
│  (time series)       │  (time series)       │
├──────────────────────┼──────────────────────┤
│  Latency Percentiles │  Active Connections  │  ← Time series
│  (P50/P95/P99)       │  (time series)       │
├──────────────────────┴──────────────────────┤
│  Recent Alerts & Incidents                  │  ← Event list
└─────────────────────────────────────────────┘
```

### Dashboard 2: AI Metrics

```
┌─────────────────────────────────────────────┐
│  [AI Queries/min]  [Avg Cost]  [Quality]    │  ← Single stat row
├──────────────────────┬──────────────────────┤
│  AI Latency          │  Token Usage         │  ← Time series
│  (time series)       │  (histogram)         │
├──────────────────────┼──────────────────────┤
│  Daily AI Spend      │  Hallucination Rate  │  ← Cumulative + %
│  (vs budget)         │  (time series)       │
├──────────────────────┴──────────────────────┤
│  User Feedback (thumbs up/down over time)   │  ← Stacked area
└─────────────────────────────────────────────┘
```
