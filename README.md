# Project Bootstrap

A platform-agnostic Agent Skill for planning production-ready software projects **before major implementation begins**.

> **Version:** 1.1.0  
> **Status:** Public / reusable  
> **License:** MIT

Project Bootstrap scales its planning depth from prototypes to large production and mission-critical systems without forcing enterprise complexity onto simple projects.

## Core workflow

```text
Product Requirements
        ↓
Scale & Criticality Classification
        ↓
Non-Functional Requirements
        ↓
Stack Detection
        ↓
Architecture
        ↓
Security + Data + Auth + Contracts
        ↓
Environments + Reliability + Observability
        ↓
CI/CD + Release + Rollback
        ↓
Quality Gates
        ↓
Architecture Decisions
        ↓
Implementation Roadmap
        ↓
Approval
        ↓
Incremental Build
```

## What makes v1.1 suitable for larger projects

The skill now adds explicit guidance for project tiering, measurable NFRs, security trust boundaries, data lifecycle and tenancy, API contracts, scalability, failure handling, environment separation, observability, CI/CD, rollback/forward-fix, and lightweight Architecture Decision Records (ADRs).

It does **not** assume that a large system requires microservices, Kubernetes, Redis, queues, or event-driven architecture. Infrastructure must solve a concrete requirement.

## Supported project types

- Lovable + React/TypeScript
- React/TypeScript applications
- Flutter/Dart mobile applications
- Backend/API systems
- Supabase-backed applications
- SaaS and multi-tenant systems
- Internal tools
- Larger production systems with multiple integrations and operational requirements

The core is framework-agnostic and loads only the references relevant to the detected stack and project tier.

## Flutter approach

For greenfield Flutter projects, the skill follows Flutter's recommended separation of UI and data responsibilities and favors a View/ViewModel/Repository/Service style when it fits. It does not force Riverpod, BLoC, or another state-management package without a project reason. Existing projects keep their established conventions unless requirements justify change.

## Use with other skills

Project Bootstrap owns **initial planning and architecture**. Specialist skills should own deep domain validation.

For example, when Supabase is selected, use a dedicated Supabase skill for detailed RLS, Auth, SQL, migrations, indexes, Storage, and Edge Function validation. After implementation, use a production code-review skill as a release/review gate.

## Example requests

```text
Bootstrap a new multi-tenant SaaS for 3 business roles. Plan first and do not code until I approve the architecture.
```

```text
Plan a Flutter mobile app with offline support, Supabase Auth, and background synchronization. Classify its production tier and define the architecture and quality gates.
```

```text
Design the bootstrap plan for a high-criticality internal platform with staging, audit requirements, external integrations, rollback, and monitoring.
```

## Installation

### Lovable

Open your workspace and go to:

**Settings -> Skills -> Import -> GitHub**

Paste:

```text
https://github.com/muhammedelessi/project-bootstrap-skill
```

### Cursor

Copy or clone this repository into a supported skill location for your Cursor version. Common project-level locations include `.agents/skills/` or `.cursor/skills/`.

### VS Code / GitHub Copilot

Place the skill in a supported Agent Skills directory for your setup, such as `.github/skills/` or `.agents/skills/` where supported.

### OpenAI Codex

Install or expose the complete skill directory to Codex so that `SKILL.md` remains the entrypoint. Follow the current Codex Agent Skills documentation for the exact supported installation path in your environment.

### Google Antigravity

Place the skill in the Agent Skills location supported by your Antigravity setup. Installation paths can vary by product/version, so prefer current product documentation over hard-coded assumptions.

### Other Agent Skills-compatible tools

Place the complete skill directory in the tool's supported skills location so `SKILL.md` remains the entrypoint. The core workflow is portable even when discovery and installation differ between tools.

## Repository structure

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
└── references/
    ├── architecture.md
    ├── stack-detection.md
    ├── project-scale.md
    ├── non-functional-requirements.md
    ├── security-design.md
    ├── data-lifecycle.md
    ├── api-contracts.md
    ├── scalability.md
    ├── reliability.md
    ├── environments.md
    ├── observability.md
    ├── cicd-release.md
    ├── architecture-decisions.md
    ├── quality-gates.md
    ├── lovable-react.md
    ├── react-typescript.md
    ├── flutter-dart.md
    ├── backend-api.md
    ├── supabase.md
    └── sources.md
```

## Design principle

Scale rigor with risk. Avoid enterprise ceremony for simple prototypes, and avoid prototype shortcuts for critical systems.

## Contributing

Issues and pull requests are welcome. See `CONTRIBUTING.md`.
