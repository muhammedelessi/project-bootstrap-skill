# Supabase Bootstrap Integration

Use this file only to coordinate project bootstrap decisions. Prefer a dedicated Supabase skill for detailed Supabase implementation and validation.

## Before UI wiring

Define:

- tables/entities and relationships
- ownership model
- authenticated roles and allowed actions
- public data surfaces
- RLS policy intent
- Storage ownership/access if files are involved
- Edge Function/server-only responsibilities
- migration order

## Security boundaries

Authentication identifies the caller; authorization decides what that caller may do. Design both explicitly.

Enable and verify RLS for exposed application data. Do not rely on client-side filters for authorization.

Never expose privileged/service-role credentials in browser or mobile clients.

Treat user-editable profile metadata as untrusted for authorization decisions.

## Migrations

Use migrations for schema and policy changes. Plan backward-compatible changes when deployment order matters. Define how to verify and, where practical, roll back or forward-fix a failed migration.

## Specialist delegation

If `supabase-agent-skill` or another dedicated Supabase skill is available, invoke it for:

- schema design
- SQL
- RLS and grants
- Auth
- Storage
- Edge Functions
- indexes and query performance
- migrations
- Supabase-specific debugging

Project Bootstrap remains responsible for sequencing and architecture; the Supabase specialist remains responsible for platform correctness.
