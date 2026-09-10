# Project Scale and Criticality

Classify engineering depth from risk and complexity, not from a single metric such as user count.

## Classification dimensions

Consider:

- Business impact of downtime or incorrect behavior
- Data sensitivity, privacy, financial impact, or regulatory exposure
- Traffic pattern, concurrency, burstiness, and workload unpredictability
- Number and criticality of external integrations
- Number of clients/platforms and compatibility obligations
- Team size, ownership boundaries, and deployment independence needs
- Recovery time expectations and data-loss tolerance
- Geographic, multi-region, offline, or realtime requirements

Use the highest materially relevant dimension to avoid understating risk.

## Tiers

### Prototype

Optimize for learning and reversibility. Require a clear core flow, simple architecture, basic validation, obvious secret boundaries, and minimal smoke testing. Do not add production infrastructure unless it is part of what must be validated.

### Standard production

Require explicit auth/authorization boundaries, persistent-data migration discipline, development and production separation, automated quality checks, error visibility and operational ownership, and deployment verification with rollback/forward-fix thinking.

### Large or high-criticality production

Require explicit NFRs, architecture decision records for costly choices, defined observability and alerts, failure-mode and dependency analysis, capacity/scalability assumptions, environment promotion strategy, data backup/restore expectations, stronger release controls, and ownership boundaries across teams or modules.

### Mission-critical

Use when failure can cause severe financial, safety, legal, regulatory, or business-continuity impact. Require measurable reliability objectives, explicit recovery targets, disaster-recovery strategy, auditability and access controls, tested recovery procedures where feasible, change-management safeguards, and specialist human review for security, reliability, compliance, and irreversible data decisions.

Do not let the skill itself certify a mission-critical system as safe or compliant.

## Anti-overengineering rule

A higher tier increases the rigor of decisions, verification, and operations. It does not automatically require microservices, Kubernetes, Redis, queues, multiple regions, or event-driven architecture.
