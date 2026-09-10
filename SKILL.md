---
name: project-bootstrap
description: Plan and bootstrap new software projects before significant implementation. Use for greenfield web, mobile, backend, API, SaaS, internal-tool, Lovable, React/TypeScript, Flutter/Dart, and Supabase projects when the user wants to start a project, choose an architecture, define folders/modules, model data, design auth and roles, select integrations, identify risks, or create a phased implementation plan. Detect the stack, load only the relevant framework references, produce a concrete architecture and build plan, and stop for approval before major implementation unless the user has already explicitly approved the plan. Do not use for routine feature work or refactoring an established project.
---

# Project Bootstrap

Bootstrap new projects deliberately instead of generating a large codebase from a single prompt.

Use this workflow:

1. Understand the product and constraints.
2. Detect or select the stack.
3. Define architecture and module boundaries.
4. Define data, auth, roles, integrations, and operational constraints.
5. Define quality gates and critical flows.
6. Produce a phased implementation plan.
7. Stop for approval before major implementation.
8. After approval, build incrementally and verify each phase.

## 1. Confirm this is a bootstrap task

Use this skill for a new project or a project that is still at the architecture/setup stage.

If the project already has substantial working code and the request is cleanup or restructuring, use a refactoring workflow instead. If the request is only to add a small feature, follow the existing project architecture rather than redesigning it.

## 2. Capture the project brief

Extract or ask only for information that materially affects architecture:

- product goal and primary users
- platforms: web, mobile, backend, desktop, API
- critical user journeys
- authentication requirements
- roles and permission boundaries
- data sensitivity and compliance constraints
- external integrations
- expected scale and performance needs
- offline, realtime, background-job, or notification requirements
- localization, RTL, accessibility, or multi-tenant requirements
- deployment and environment constraints

Do not block on minor details. State reasonable assumptions explicitly and mark them as assumptions.

## 3. Detect or select the stack

Inspect the user's stated requirements and any existing project metadata.

- If the stack is already chosen, respect it unless it creates a concrete conflict with requirements.
- If the stack is not chosen and the choice materially affects the architecture, present one primary recommendation and at most one credible alternative with tradeoffs, then wait for the user when necessary.
- Avoid adding frameworks, state libraries, ORMs, queues, or infrastructure without a demonstrated need.
- Prefer boring, well-supported defaults over novelty.

Load the relevant references:

- General architecture: [references/architecture.md](references/architecture.md)
- Stack detection and selection: [references/stack-detection.md](references/stack-detection.md)
- React + TypeScript: [references/react-typescript.md](references/react-typescript.md)
- Lovable + React projects: [references/lovable-react.md](references/lovable-react.md)
- Flutter + Dart: [references/flutter-dart.md](references/flutter-dart.md)
- Backend/API projects: [references/backend-api.md](references/backend-api.md)
- Supabase projects: [references/supabase.md](references/supabase.md)
- Quality gates: [references/quality-gates.md](references/quality-gates.md)

## 4. Define architecture before implementation

Design the smallest architecture that cleanly supports the requirements.

Always define:

- system boundaries and major modules/features
- dependency direction
- UI, business/domain, data-access, and integration responsibilities where relevant
- state ownership
- API/data flow
- error and loading behavior
- configuration and secrets boundaries
- persistence and migration approach
- background/realtime workflows if required
- logging, monitoring, and failure recovery expectations

Prefer a modular monolith by default for ordinary greenfield products. Introduce services or distributed components only when scale, isolation, deployment, ownership, or reliability requirements justify them.

## 5. Define data, auth, and protected boundaries

Before building authenticated or data-driven features, define:

- core entities and relationships
- source of truth for each entity
- ownership model
- user roles and allowed actions
- server-side authorization boundaries
- public vs authenticated vs privileged data
- migration strategy
- retention/deletion rules when relevant
- external API and webhook contracts

Do not treat UI visibility as authorization.

If Supabase is used, load [references/supabase.md](references/supabase.md). If a dedicated Supabase skill is available, use it for schema, Auth, RLS, SQL, migrations, Storage, Edge Functions, indexes, and database-specific validation rather than duplicating that specialist guidance here.

## 6. Define quality gates before coding

Use [references/quality-gates.md](references/quality-gates.md).

At minimum, define:

- critical flows that must work
- unit/integration/widget/end-to-end coverage appropriate to the stack
- lint/static-analysis/typecheck expectations
- production build verification
- auth/role negative tests
- migration and rollback checks where data is involved
- smoke tests for deployment

Do not postpone all testing until the end.

## 7. Produce the bootstrap plan

Return a concrete plan with these sections:

### Project brief
Summarize the product, users, and critical flows.

### Stack
State the selected stack and why it fits. Include unresolved decisions only when they materially affect implementation.

### Architecture
Show the main modules/layers, dependency direction, and data flow. Include a proposed folder/module structure when useful.

### Data and security
Describe entities, auth model, roles, authorization boundaries, sensitive data, and integrations.

### Implementation phases
Break work into small vertical phases. Each phase should leave the project in a coherent, testable state.

### Quality gates
State what must pass after each phase and before release.

### Risks and assumptions
Separate confirmed constraints from assumptions. Call out architecture decisions that would be costly to reverse later.

### Approval gate
End with a clear statement that implementation has not started yet and identify the first proposed phase.

## 8. Stop before major implementation

Do not generate or modify a broad production codebase during the initial bootstrap plan.

Wait for explicit approval before major implementation unless the user already gave an unambiguous instruction to proceed with the planned architecture.

After approval:

1. Implement one phase at a time.
2. Keep changes scoped to that phase.
3. Run the applicable quality gates.
4. Report what changed and what remains.
5. Re-plan only if new evidence invalidates an architectural assumption.

## Core guardrails

- Do not invent requirements to justify complexity.
- Do not create microservices by default.
- Do not introduce global state when local or feature state is sufficient.
- Do not couple UI directly to persistence or privileged backend operations when a clear boundary is needed.
- Do not hard-code secrets or environment-specific values.
- Do not mix unrelated architecture migrations into initial feature delivery.
- Do not claim production readiness without meaningful verification.
- Preserve framework conventions unless there is a concrete reason not to.
- Favor reversible decisions early; document irreversible or expensive decisions explicitly.
