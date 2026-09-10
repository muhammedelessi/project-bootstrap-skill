# API and Integration Contracts

Use for HTTP APIs, RPC, webhooks, queues, third-party integrations, and multiple application clients.

## Contract basics

Define ownership and consumers, authentication and authorization, request validation, response/error model, compatibility/evolution policy, pagination for unbounded collections, rate/usage constraints where relevant, and timeouts.

## Mutating operations

For operations that may be retried or repeated, evaluate idempotency. Financial, provisioning, order, email-trigger, and external-side-effect operations often need an idempotency strategy.

## Retries

Do not add retries blindly. Define retryable vs non-retryable failures, bounded attempts, backoff/jitter where relevant, overall timeout/deadline, and duplicate-side-effect protection.

## Webhooks

When receiving webhooks, verify authenticity/signatures using provider guidance, consider replay protection, acknowledge quickly when provider retry behavior requires it, move long work out of the request path when necessary, and make processing idempotent if delivery can repeat.

## Versioning

Prefer additive/backward-compatible contract evolution when practical. Introduce explicit API versioning only when compatibility obligations justify it.
