# Deployment Architecture

## Infrastructure

*Describe the infrastructure supporting the deployment.*

| Resource | Specification | Provider | Purpose |
|----------|--------------|----------|---------|
| *e.g., Compute* | *4 vCPU, 16 GB RAM* | *AWS EC2 / GCP GCE / Azure VM* | *Application servers* |
| *e.g., Container Orchestration* | *Kubernetes cluster, 3 nodes* | *EKS / GKE / AKS* | *Service orchestration* |
| *e.g., GPU Instances* | *1x A100, 80 GB VRAM* | *AWS p4d / GCP a2* | *Model inference (if self-hosted)* |
| *e.g., Database* | *db.r6g.xlarge, 500 GB* | *RDS / Cloud SQL / CosmosDB* | *Primary data store* |
| *e.g., CDN* | *Global edge locations* | *CloudFront / Cloud CDN* | *Static asset delivery* |
| *e.g., Load Balancer* | *Application LB* | *ALB / Cloud Load Balancing* | *Traffic distribution* |
| | | | |

### Network Architecture

*Describe VPC layout, subnets, security groups, and network policies.*

```
┌─────────────────────────────────────────────────┐
│  VPC: 10.0.0.0/16                               │
│  ┌───────────────────┐  ┌────────────────────┐  │
│  │ Public Subnet      │  │ Public Subnet      │  │
│  │ 10.0.1.0/24       │  │ 10.0.2.0/24       │  │
│  │ [Load Balancer]   │  │ [NAT Gateway]      │  │
│  └───────────────────┘  └────────────────────┘  │
│  ┌───────────────────┐  ┌────────────────────┐  │
│  │ Private Subnet     │  │ Private Subnet     │  │
│  │ 10.0.3.0/24       │  │ 10.0.4.0/24       │  │
│  │ [App Servers]     │  │ [Database]         │  │
│  └───────────────────┘  └────────────────────┘  │
└─────────────────────────────────────────────────┘
```

*Modify this diagram to reflect your actual network topology.*

## Environments

| Environment | Purpose | URL/Endpoint | Data | Who Has Access |
|-------------|---------|-------------|------|----------------|
| **Development** | *Local dev and feature testing* | *localhost / dev.example.com* | *Synthetic/seed data* | *Engineering team* |
| **Staging** | *Pre-production validation* | *staging.example.com* | *Anonymized production mirror* | *Engineering + QA* |
| **Production** | *Live customer traffic* | *app.example.com* | *Real customer data* | *SRE + on-call engineers* |

### Environment Parity

*How do you ensure environments are consistent?*

- **Infrastructure as Code:** *e.g., Terraform modules shared across environments with environment-specific tfvars*
- **Configuration management:** *e.g., Environment variables via AWS SSM / GCP Secret Manager*
- **Data strategy:** *How staging data mirrors production without exposing PII*
- **Feature flags:** *e.g., LaunchDarkly / Unleash for progressive rollout*

## CI/CD Pipeline

*Document your continuous integration and deployment pipeline.*

```
┌────────┐   ┌────────┐   ┌─────────┐   ┌──────────┐   ┌────────────┐
│  Code  │──▶│ Build  │──▶│  Test   │──▶│  Stage   │──▶│ Production │
│  Push  │   │        │   │         │   │  Deploy  │   │  Deploy    │
└────────┘   └────────┘   └─────────┘   └──────────┘   └────────────┘
```

### Pipeline Stages

| Stage | Tools | Actions | Gate Criteria |
|-------|-------|---------|--------------|
| **Build** | *e.g., Docker, GitHub Actions* | *Compile, lint, build container image* | *Build succeeds, no lint errors* |
| **Unit Test** | *e.g., pytest, Jest* | *Run unit test suite* | *100% pass, coverage > X%* |
| **Integration Test** | *e.g., pytest + testcontainers* | *Test cross-service interactions* | *All integration tests pass* |
| **Security Scan** | *e.g., Snyk, Trivy, Semgrep* | *Vulnerability scanning, SAST* | *No critical/high vulnerabilities* |
| **AI Evaluation** | *e.g., Custom eval suite* | *Run prompt regression tests, eval benchmarks* | *Accuracy >= baseline, no regressions* |
| **Deploy to Staging** | *e.g., ArgoCD, Helm* | *Deploy to staging environment* | *Health checks pass* |
| **Smoke Test** | *e.g., Playwright, curl* | *Verify critical paths in staging* | *All smoke tests pass* |
| **Deploy to Production** | *e.g., ArgoCD, blue-green* | *Progressive rollout to production* | *Manual approval + automated checks* |

### Deployment Strategy

- **Strategy:** *e.g., Blue-green / Canary / Rolling update*
- **Rollback procedure:** *How to revert a bad deployment*
- **Deployment frequency:** *e.g., Multiple times per day / Weekly*

## Monitoring

| Category | Tool | What It Monitors | Alert Channel |
|----------|------|-----------------|---------------|
| **Infrastructure** | *e.g., Datadog / CloudWatch* | *CPU, memory, disk, network* | *PagerDuty / Slack* |
| **Application** | *e.g., Datadog APM / New Relic* | *Request latency, error rates, throughput* | *Slack #alerts* |
| **AI/ML** | *e.g., Custom dashboards* | *Model latency, token usage, hallucination rate* | *Slack #ai-monitoring* |
| **Logs** | *e.g., ELK / Datadog Logs* | *Application logs, error tracking* | *Automated triage* |
| **Uptime** | *e.g., Pingdom / UptimeRobot* | *Endpoint availability* | *PagerDuty* |

### Key Dashboards

- *Link or description of primary operations dashboard*
- *Link or description of AI-specific metrics dashboard*
- *Link or description of cost monitoring dashboard*

### On-Call

- **Rotation:** *e.g., Weekly rotation among N engineers*
- **Runbook location:** *Link to runbooks*
- **Escalation path:** *On-call engineer -> Tech Lead -> Engineering Manager*

## Scaling Strategy

### Horizontal Scaling

| Component | Scaling Trigger | Min Instances | Max Instances | Scale-Up Time |
|-----------|----------------|---------------|---------------|--------------|
| *e.g., API servers* | *CPU > 70%* | *2* | *10* | *~2 min* |
| *e.g., Worker nodes* | *Queue depth > 100* | *1* | *5* | *~3 min* |
| | | | | |

### Vertical Scaling

*Document any components that scale vertically and their upgrade path.*

### AI-Specific Scaling Considerations

- **Model inference:** *How do you handle spikes in AI requests? (e.g., request queuing, rate limiting, auto-scaling inference servers)*
- **Token budget:** *How do you manage API costs as traffic scales?*
- **Caching:** *What AI responses are cacheable to reduce inference load?*
- **Rate limiting:** *Per-user and global rate limits for AI endpoints*

### Cost Estimation

| Component | Monthly Cost (Dev) | Monthly Cost (Staging) | Monthly Cost (Prod) |
|-----------|--------------------|----------------------|---------------------|
| *Compute* | *$__* | *$__* | *$__* |
| *Database* | *$__* | *$__* | *$__* |
| *AI API calls* | *$__* | *$__* | *$__* |
| *Storage* | *$__* | *$__* | *$__* |
| **Total** | **$__** | **$__** | **$__** |
