# Bootstrap Quality Gates

Define quality gates before implementation so the project does not accumulate an untestable foundation.

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

Identify a small set of critical flows early. Examples:

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

- verify migration order
- verify required indexes/constraints
- test representative existing data when possible
- verify authorization policies after schema changes
- identify rollback or forward-fix strategy

## Release baseline

Do not label the project production-ready until the production build succeeds and critical flows have meaningful verification in an environment representative of deployment.
