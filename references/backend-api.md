# Backend and API Bootstrap

## API contract first

Define the contract before broad implementation:

- routes/operations
- authentication requirements
- authorization rules
- request validation
- response schema
- error model
- pagination/filtering/sorting where relevant
- idempotency expectations for retryable writes
- versioning or compatibility constraints when public/external

## Boundaries

Separate transport/controller concerns from business/application logic and persistence/integration code. Do not place complex business rules directly in route handlers.

## Validation and authorization

Validate all untrusted inputs at runtime. Perform authorization server-side at the resource/action boundary. Never rely on hidden buttons or client-side role checks as security.

## Reliability

For external calls and background jobs, define timeout, retry, idempotency, dead-letter/failure handling, and observability behavior when relevant.

Avoid automatic retries for operations that are not safe to repeat.

## Data changes

Use explicit migrations for persistent schema changes. Identify backward-compatibility needs when multiple application versions may overlap during deployment.

## Operational baseline

Plan structured error logging, health checks, environment configuration, rate limiting/abuse controls when public, and safe shutdown/resource cleanup where the runtime requires it.
