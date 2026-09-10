# CI/CD, Release, and Rollback

Treat delivery as part of the architecture for production systems.

## Continuous integration

Before merge/release, run applicable checks automatically where practical: formatting/lint, static analysis/typecheck, tests relevant to changed boundaries, production build, dependency/security checks used by the project, and migration validation when applicable.

## Promotion

Define how changes move from development to production. High-risk systems should avoid unreviewed direct production changes.

## Database-aware releases

Keep application and schema compatible during rollout when deployment is not atomic. Prefer expand/migrate/contract patterns for risky production changes.

## Rollback and forward-fix

Before a risky release, know whether rollback is safe. Schema/data changes may make code rollback unsafe; in that case define a forward-fix path.

## Progressive delivery

Use feature flags, canaries, or staged rollout only when blast-radius reduction justifies the operational complexity. Define ownership and flag cleanup.

## Dependencies

Do not combine major framework/library upgrades with unrelated initial delivery. Pin or constrain critical dependencies according to ecosystem conventions and review high-impact upgrades deliberately.
