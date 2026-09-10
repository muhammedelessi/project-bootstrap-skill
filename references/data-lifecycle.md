# Data Lifecycle and Tenancy

Design data ownership and recovery before schema implementation.

## Source of truth

For each important entity define the authoritative system/store, owner or tenant, writers and readers, consistency expectations, and any external synchronization. Avoid multiple uncontrolled sources of truth.

## Multi-tenancy

If multi-tenant, choose the tenant identifier and ownership model, define tenant isolation at trusted backend/database boundaries, define cross-tenant admin/support behavior explicitly, test denial of cross-tenant access, and avoid relying on client-side tenant filtering.

## Lifecycle

Define creation/update ownership, soft-delete vs hard-delete semantics, retention period, archival, export requirements, and account/tenant deletion flow when relevant.

## Backup and recovery

For production data, identify what is backed up, the expected restore mechanism, recovery target assumptions, whether restore is tested, and which external data cannot be reconstructed.

Do not claim backup is effective merely because a provider advertises backups; confirm plan/configuration and restore behavior before relying on it.

## Migrations

Prefer backward-compatible, staged migrations for production systems. Separate schema rollout, data backfill, application cutover, and cleanup when a single atomic change would be risky.
