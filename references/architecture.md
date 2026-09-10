# Architecture Guidance

## Default decision model

Start with the simplest architecture that preserves clear boundaries and can evolve without a rewrite.

For most ordinary product applications, prefer a modular monolith over microservices. Split deployable services only when there is a concrete need such as independent scaling, strict fault isolation, separate ownership, distinct security boundaries, or independent release cadence.

## Boundaries

Define responsibilities before folders.

Typical boundaries include presentation/UI, application or orchestration logic, domain/business rules when substantial, data access and persistence, external integrations, and platform/infrastructure concerns.

Dependencies should point toward stable abstractions rather than allowing every feature to call infrastructure directly.

## Feature organization

Prefer feature-oriented organization when it helps developers locate everything related to one business capability. Keep truly shared infrastructure in a small core/shared area. Do not create a large generic `utils` directory as a dumping ground.

## State and data flow

Identify a single owner/source of truth for important state. Avoid duplicated derived state. Keep remote/server state distinct from transient UI state when useful.

Map each critical flow from user action to validation, authorization, persistence/integration, response, and UI feedback.

## Error handling

Define error behavior at boundaries: validation errors, authorization failures, network/service failures, timeouts and retries, partial failures, duplicate/replayed requests, and background job failures.

Do not hide failures behind generic success messages.

## Configuration and secrets

Keep environment configuration explicit. Secrets must stay outside public clients and source control. Validate required configuration at startup or deployment where practical.

## Observability

For production-bound systems, decide early how to capture structured application errors, request/job correlation where relevant, health signals, meaningful audit events for privileged actions, and performance bottlenecks.

Avoid logging secrets, credentials, or unnecessary personal data.

## Reversibility

Prefer decisions that can be changed later without data loss. Treat database shape, public API contracts, auth identity model, tenancy model, and external webhook contracts as high-cost decisions that deserve explicit review.
