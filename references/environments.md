# Environments and Configuration

Separate production risk from everyday development.

## Environment model

Choose the minimum model justified by the project:

- Prototype: local/preview may be enough if no production data is involved.
- Standard production: development/testing plus production separation is normally expected.
- Large/high-criticality: add staging/pre-production when it materially reduces release, integration, or migration risk.

Do not create environments only for ceremony.

## Configuration

- Keep environment-specific values outside source logic.
- Validate required configuration at startup/build time when possible.
- Do not commit secrets.
- Use separate credentials per environment.
- Restrict production access to the minimum operational need.

## Data

Do not copy sensitive production data into lower environments without an explicit safe process. Prefer synthetic, masked, or minimal test data.

## Migrations

Define how migrations move through environments and how application/database compatibility is preserved during rollout.
