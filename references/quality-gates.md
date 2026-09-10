# Bootstrap Quality Gates

Define quality gates before implementation so the project does not accumulate an untestable or unoperable foundation.

## Per-phase gates

After each implementation phase, run the checks that exist for the stack:

- formatter
- lint/static analysis
- typecheck
- relevant unit/component/widget tests
- integration tests for changed boundaries
- production build
- manual smoke test of the newly completed flow

Record pre-existing failures separately from regressions introduced by the phase.

## Critical-flow coverage

Identify critical flows early. Examples:

- sign up/sign in/sign out
- password/session recovery
- role-restricted action
- create/update/delete of core business data
- payment or checkout
- file upload/download
- external webhook/integration
- offline/reconnect or realtime flow

Test both allowed and denied paths for protected actions.

## Data and migration gates

For persistent data changes:

- verify migration order and application compatibility
- verify required indexes/constraints
- test representative existing data when possible
- verify authorization policies after schema changes
- identify rollback or forward-fix strategy
- verify backup/restore assumptions for high-risk changes

## Performance gates

For projects with explicit performance NFRs, define representative measurements before release. Do not use arbitrary budgets disconnected from requirements.

## Security gates

For authenticated/data-driven systems, verify negative authorization cases, secret exposure, privileged paths, and dependency/security tooling already adopted by the project.

## Operational gates

For production systems verify:

- production configuration is complete
- required telemetry is present
- deployment smoke checks exist
- rollback/forward-fix path is understood
- alerts have owners for high-criticality services

## Release baseline

Do not label the project production-ready until the production build succeeds and critical flows have meaningful verification in an environment representative of deployment.

For Large/high-criticality or Mission-critical systems, production readiness also requires the relevant NFR, observability, recovery, and release controls to be verified rather than merely documented.
