# Security Design Pass

Perform a lightweight architecture-level security pass before implementation.

## Identify boundaries

Map users, admins, operators, service identities, external systems, public vs authenticated entry points, privileged operations, data stores, sensitive data classes, trust transitions, secrets, and inbound webhooks/callbacks.

## Authorization

Define authorization at the trusted enforcement boundary. UI hiding is not authorization.

For each privileged or data-mutating action, identify who may perform it, on which resource or tenant, which server/database policy enforces it, and which negative test proves denial works.

## Abuse cases

For critical flows, consider plausible misuse such as IDOR/resource ownership bypass, privilege escalation, replayed or forged webhooks, duplicate financial/data mutation, unlimited expensive operations, untrusted uploads, and secret leakage through client code or logs.

## Escalation

For regulated, financial, identity-heavy, or mission-critical systems, recommend a dedicated security review/threat model. This reference is architecture hygiene, not a security certification.
