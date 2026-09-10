# Stack Detection and Selection

## Detect an existing choice

Inspect the request and repository metadata before recommending anything. Examples include package manifests, lockfiles, framework configuration, platform folders, database configuration, and deployment files.

Do not replace an already-selected stack merely because another option is preferred.

## Selecting a stack for a greenfield project

Choose based on requirements rather than popularity alone.

Consider target platforms, team familiarity, ecosystem maturity, deployment constraints, realtime/offline needs, native device integrations, SEO/server-rendering requirements, data and authorization model, expected scale, and testability/maintainability.

## Decision rule

If one stack clearly fits, recommend it and explain the main reason.

If two options are genuinely close and the decision is expensive to reverse, present one primary recommendation plus one alternative and ask the user to choose.

Avoid presenting long menus of frameworks.

## Dependency restraint

Every added dependency should solve a concrete problem. Prefer platform/framework capabilities when they are sufficient. Do not introduce state management, dependency injection, ORMs, queues, caches, or service meshes preemptively.
