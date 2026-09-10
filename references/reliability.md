# Reliability and Failure Design

Design critical paths for predictable failure, not only happy-path success.

## Dependency map

For each critical external dependency identify timeout, failure behavior, retry policy, fallback or degraded behavior, data consistency impact, and observability signal.

## Retry discipline

Use retries only for failures likely to be transient. Keep retries bounded and protect repeated side effects with idempotency where required.

## Graceful degradation

Prefer preserving safe core behavior when a non-critical dependency fails. Do not hide failures that would make data incorrect or unsafe.

## Recovery

For persistent workflows define retry/reconciliation mechanism, stuck-work visibility, manual recovery path for high-value operations, and rollback vs forward-fix policy.

## Reliability objectives

For high-criticality systems, capture availability and recovery objectives when the business provides them. Never invent SLA/SLO targets or claim they are met before measurement.
