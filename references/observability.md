# Observability

Define enough telemetry to detect, diagnose, and own production failures.

## Logs

Use structured, contextual logs for important operations. Include correlation/request identifiers when useful across boundaries.

Never log passwords, secret keys, raw access/refresh tokens, or unnecessary personal/sensitive payloads.

## Errors

Use actionable error tracking. Capture stack/context appropriate to the platform without exposing sensitive data.

## Metrics

For critical paths, prefer signals that answer:

- Is it available?
- Is it slow?
- Is it failing?
- Is a dependency saturated?
- Is asynchronous work backing up?

For high-criticality workflows, add business/process outcome signals when appropriate.

## Alerts

An alert should have an owner and an action. Avoid noisy alerts with no response path.

For large systems, document dashboard/alert expectations before release, but do not invent operational thresholds without evidence or business targets.
