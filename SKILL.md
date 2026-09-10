---
name: project-bootstrap
description: Plan and bootstrap new software projects before significant implementation, from prototypes to large production and mission-critical systems. Use for greenfield web, mobile, backend, API, SaaS, internal-tool, Lovable, React/TypeScript, Flutter/Dart, and Supabase projects when the user wants to start a project, choose architecture, define modules, model data, design auth and roles, select integrations, identify risks, define non-functional requirements, plan environments, observability, CI/CD, release and rollback, or create a phased implementation roadmap. Classify project scale and criticality, detect the stack, load only relevant references, produce a concrete architecture and delivery plan, and stop for approval before major implementation unless already explicitly approved. Do not use for routine feature work or refactoring an established project.
---

# Project Bootstrap

Bootstrap new projects deliberately instead of generating a large codebase from a single prompt.

Use this workflow:

1. Understand the product and constraints.
2. Classify project scale and criticality.
3. Define non-functional requirements.
4. Detect or select the stack.
5. Define architecture and module boundaries.
6. Define security, data, auth, roles, integrations, and contracts.
7. Define environments, reliability, observability, and release strategy.
8. Define quality gates and critical flows.
9. Record high-impact architecture decisions.
10. Produce a phased implementation roadmap.
11. Stop for approval before major implementation.
12. After approval, build incrementally and verify each phase.

## 1. Confirm this is a bootstrap task

Use this skill for a new project or a project still at architecture/setup stage.

If substantial working code already exists and the request is cleanup or restructuring, use a refactoring workflow instead. If the request is only a small feature, follow the established project architecture rather than redesigning the system.

## 2. Capture the project brief

Extract or ask only for information that materially affects architecture:

- product goal and primary users
- platforms: web, mobile, backend, desktop, API
- critical user journeys
- authentication requirements
- roles and permission boundaries
- data sensitivity and compliance constraints
- external integrations
- expected scale, traffic shape, concurrency, and performance needs
- availability, recovery, and business-criticality expectations
- offline, realtime, background-job, or notification requirements
- localization, RTL, accessibility, or multi-tenant requirements
- deployment, team, ownership, and environment constraints

Do not block on minor details. State reasonable assumptions explicitly and mark them as assumptions.

## 3. Classify scale and criticality

Load [references/project-scale.md](references/project-scale.md).

Classify the project using business impact, data sensitivity, traffic/concurrency, integration complexity, team/ownership, and recovery expectations. Do not classify scale from user count alone.

Use the classification to control engineering depth:

- Prototype: optimize for learning and reversibility.
- Standard production: require baseline security, testing, environments, monitoring, and rollback.
- Large/high-criticality production: require explicit NFRs, observability, failure design, CI/CD controls, data recovery, and decision records.
- Mission-critical: require measurable reliability objectives, disaster-recovery planning, auditability, stricter change controls, and specialist/human review for high-risk decisions.

Do not introduce enterprise infrastructure merely because the label is "large".

## 4. Define non-functional requirements

Load [references/non-functional-requirements.md](references/non-functional-requirements.md).

Capture only requirements that influence design. For material requirements, define an objective or measurable target where possible:

- latency and throughput
- availability and recovery objectives
- data durability and retention
- security and privacy
- scalability and concurrency
- accessibility and localization
- cost constraints
- operability and supportability

Do not invent numeric SLOs. If the user has not provided targets, propose explicit assumptions or decision ranges and flag them for confirmation.

## 5. Detect or select the stack

Load [references/stack-detection.md](references/stack-detection.md).

- If the stack is already chosen, respect it unless it creates a concrete conflict with requirements.
- If the stack is not chosen and the choice materially affects architecture, present one primary recommendation and at most one credible alternative with tradeoffs.
- Avoid adding frameworks, state libraries, ORMs, queues, caches, or infrastructure without demonstrated need.
- Prefer boring, well-supported defaults over novelty.
- Preserve platform conventions unless requirements justify deviation.

Load only relevant framework references:

- General architecture: [references/architecture.md](references/architecture.md)
- React + TypeScript: [references/react-typescript.md](references/react-typescript.md)
- Lovable + React: [references/lovable-react.md](references/lovable-react.md)
- Flutter + Dart: [references/flutter-dart.md](references/flutter-dart.md)
- Backend/API: [references/backend-api.md](references/backend-api.md)
- Supabase: [references/supabase.md](references/supabase.md)

## 6. Define architecture before implementation

Load [references/architecture.md](references/architecture.md).

Design the smallest architecture that cleanly supports the requirements. Define:

- system boundaries and major modules/features
- dependency direction
- UI, domain/business, data-access, and integration responsibilities where relevant
- state ownership and consistency model
- API/data flow
- error and loading behavior
- configuration and secrets boundaries
- persistence and migration approach
- background/realtime workflows if required
- ownership boundaries for large teams

Prefer a modular monolith by default for ordinary greenfield products. Introduce services or distributed components only when scale, independent deployment, isolation, ownership, or reliability requirements justify them.

Do not choose microservices, Kubernetes, Redis, queues, event buses, CQRS, or similar infrastructure because they sound "enterprise". Require a concrete problem they solve.

## 7. Design security and trust boundaries

Load [references/security-design.md](references/security-design.md).

Before implementation, identify:

- actors and trust boundaries
- privileged operations
- authentication and authorization boundaries
- sensitive data and secrets
- public, authenticated, privileged, and service-to-service surfaces
- abuse cases for critical workflows
- external dependencies and inbound webhooks

Do not treat UI visibility as authorization. Keep privileged enforcement server-side or at an equivalent trusted boundary.

For high-risk or regulated systems, recommend a dedicated threat-model/security review rather than claiming this bootstrap pass is sufficient.

## 8. Define data, tenancy, and lifecycle

Load [references/data-lifecycle.md](references/data-lifecycle.md).

Define:

- core entities and relationships
- source of truth for each entity
- ownership and tenant isolation model
- retention/deletion requirements
- backup and restore expectations
- schema migration strategy
- rollback or forward-fix approach
- audit requirements where relevant

If Supabase is used, load [references/supabase.md](references/supabase.md). If a dedicated Supabase skill is available, use it for schema, Auth, RLS, SQL, migrations, Storage, Edge Functions, indexes, and database-specific validation rather than duplicating specialist guidance here.

## 9. Define API and integration contracts

For projects with APIs, webhooks, third-party integrations, or multiple clients, load [references/api-contracts.md](references/api-contracts.md).

Define contract ownership, validation, errors, pagination where needed, idempotency for repeatable writes, timeout/retry behavior, versioning/evolution policy, and webhook authenticity/replay handling.

Do not design distributed retry behavior without considering duplication and idempotency.

## 10. Define scalability and failure behavior when needed

For Large/high-criticality or workload-sensitive projects, load:

- [references/scalability.md](references/scalability.md)
- [references/reliability.md](references/reliability.md)

Plan bottlenecks and failure modes before introducing scaling infrastructure. Prefer measurement-driven evolution.

Define timeout boundaries, bounded retries, backoff, idempotency, graceful degradation, queue/backpressure behavior when applicable, and recovery paths for critical operations.

## 11. Define environments and secrets

Load [references/environments.md](references/environments.md).

Define the minimum environment model appropriate to the tier. Production systems should normally separate development/testing concerns from production data and secrets. Define configuration ownership, secret handling, migration promotion, and production access boundaries.

Avoid environment-specific behavior hidden in source code.

## 12. Define observability

For production projects, load [references/observability.md](references/observability.md).

Define what must be observable before release:

- structured logs for critical events
- actionable error tracking
- health/availability signals
- latency and saturation indicators for critical dependencies
- business or workflow signals where technically appropriate
- alert ownership and escalation for high-criticality systems

Do not log secrets, raw tokens, credentials, or unnecessary sensitive data.

## 13. Define CI/CD, release, and rollback

For production projects, load [references/cicd-release.md](references/cicd-release.md).

Define:

- required automated checks before merge/release
- environment promotion strategy
- migration ordering
- deployment verification
- rollback or forward-fix plan
- feature flags/progressive rollout only when risk justifies them
- dependency update policy for critical packages

Do not mix major dependency/framework upgrades into initial delivery unless they are required and explicitly approved.

## 14. Define quality gates before coding

Load [references/quality-gates.md](references/quality-gates.md).

At minimum define:

- critical flows that must work
- unit/integration/widget/end-to-end coverage appropriate to the stack
- lint/static-analysis/typecheck expectations
- production build verification
- auth/role negative tests
- migration and rollback checks where data is involved
- smoke tests for deployment
- performance/security/operational gates when required by the project tier

Do not postpone all testing until the end.

## 15. Record architecture decisions

For decisions that are expensive to reverse or affect multiple teams/systems, load [references/architecture-decisions.md](references/architecture-decisions.md).

Record a lightweight ADR containing context, decision, alternatives considered, consequences, status, and review trigger. Do not create ADRs for trivial choices.

## 16. Produce the bootstrap plan

Return a concrete plan with these sections:

### Project brief
Summarize the product, users, critical flows, constraints, and assumptions.

### Scale and criticality
State the project tier and the factors driving it.

### Non-functional requirements
List confirmed targets and explicit assumptions that influence architecture.

### Stack
State the selected stack and why it fits. Include unresolved decisions only when they materially affect implementation.

### Architecture
Show modules/layers, dependency direction, data flow, state ownership, and proposed folder/module structure when useful.

### Data and security
Describe entities, auth model, roles, tenant/ownership boundaries, sensitive data, lifecycle, and trust boundaries.

### Integrations and contracts
Describe external dependencies, APIs/webhooks, ownership, idempotency, and failure behavior.

### Operations and delivery
Describe environments, secrets, observability, CI/CD, deployment, rollback, and recovery expectations.

### Implementation phases
Break work into small vertical phases. Each phase should leave the project coherent and testable.

### Quality gates
State what must pass after each phase and before release.

### Architecture decisions
List ADRs required now and decisions intentionally deferred.

### Risks and assumptions
Separate confirmed constraints from assumptions. Call out decisions that would be costly to reverse later.

### Approval gate
End with a clear statement that major implementation has not started and identify the first proposed phase.

## 17. Stop before major implementation

Do not generate or modify a broad production codebase during the initial bootstrap plan.

Wait for explicit approval before major implementation unless the user already gave an unambiguous instruction to proceed with the planned architecture.

After approval:

1. Implement one phase at a time.
2. Keep changes scoped to that phase.
3. Run applicable quality, security, migration, and deployment gates.
4. Report what changed, what was verified, and what remains.
5. Record material architecture decisions.
6. Re-plan only if new evidence invalidates an assumption.

## Core guardrails

- Do not invent requirements to justify complexity.
- Do not create microservices or distributed infrastructure by default.
- Do not introduce global state when local or feature state is sufficient.
- Do not couple UI directly to persistence or privileged operations when a trusted boundary is needed.
- Do not hard-code secrets or environment-specific values.
- Do not mix unrelated architecture migrations, feature work, or major dependency upgrades into bootstrap phases.
- Do not claim production readiness without meaningful verification.
- Do not claim high availability, disaster recovery, or security guarantees without evidence.
- Favor reversible decisions early; document irreversible or expensive decisions explicitly.
- Scale controls with risk: avoid enterprise ceremony for simple prototypes, and avoid prototype shortcuts for critical systems.
