# Architecture Decision Records

Use a lightweight ADR for decisions that are costly to reverse, cross team/system boundaries, or materially affect reliability, security, or data design.

## ADR template

```text
Title:
Status: proposed | accepted | superseded
Context:
Decision:
Alternatives considered:
Consequences:
Validation/assumptions:
Review trigger:
```

## Good ADR candidates

- primary database or persistence model
- tenancy/isolation strategy
- monolith vs service boundary
- authentication architecture
- offline synchronization model
- critical third-party dependency
- event/queue architecture
- API compatibility strategy
- deployment topology for high-criticality systems

## Avoid ADR noise

Do not create ADRs for ordinary local implementation details or framework conventions that are easy to reverse.

## Review trigger

Every ADR with meaningful assumptions should state what evidence would justify revisiting it, such as traffic growth, team ownership changes, new compliance needs, or a dependency becoming unreliable.
