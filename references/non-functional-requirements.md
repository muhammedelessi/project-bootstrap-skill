# Non-Functional Requirements

Use NFRs to turn vague expectations such as "fast", "secure", and "scalable" into architecture inputs.

## Capture only material requirements

Consider:

- Performance: response latency, startup time, rendering responsiveness, throughput
- Scale: expected concurrency, dataset growth, burst traffic, background workload
- Reliability: availability, acceptable failure behavior, recovery expectations
- Data durability: acceptable data loss, backup/restore needs
- Security/privacy: sensitive data classes, access boundaries, auditability
- Compliance: only when explicitly applicable; do not infer certifications
- Accessibility/localization: target standards, languages, RTL, locale behavior
- Cost: budget ceilings or cost-sensitive workloads
- Operability: deployment frequency, support hours, incident ownership

## Make targets measurable when justified

Prefer concrete targets, but never invent them.

When missing, write an explicit assumption such as:

- "Target latency is not defined; architecture assumes ordinary interactive SaaS expectations and should be revisited before load testing."
- "No formal availability objective provided; treat this as standard production until clarified."

## Link NFRs to decisions

Every material NFR should map to one or more design consequences. Examples:

- strict recovery target -> backup/restore and recovery design
- burst traffic -> capacity, queueing, rate limiting, or autoscaling evaluation
- sensitive records -> stronger authorization, audit, retention, and observability redaction
- offline mobile -> local persistence, synchronization, conflict policy

Do not create infrastructure without the requirement-to-decision link.
