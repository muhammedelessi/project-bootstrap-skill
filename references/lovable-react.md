# Lovable + React Bootstrap

Use this guidance when the project is being created in Lovable.

## Respect Lovable context

Treat Workspace Knowledge and Project Knowledge as architecture inputs. Do not duplicate permanent workspace coding standards inside the project bootstrap plan; reference them and add only project-specific decisions.

Use planning before broad generation. Define routes, features, data model, auth model, integrations, and critical flows before asking the agent to build many screens at once.

## Project structure

Prefer feature-oriented React/TypeScript structure with clear separation between presentation, feature logic, data access, and integrations. Reuse components when semantics are actually shared, not merely because markup looks similar.

Keep business rules and privileged operations out of client-only UI code.

## Supabase

When Lovable uses Supabase, load `supabase.md` and use a dedicated Supabase skill if available. Define schema, ownership, authorization, and RLS before wiring broad UI access.

Do not assume authentication alone protects database rows.

## Incremental delivery

Build one coherent vertical slice at a time: route/screen, data contract, authorization, persistence/integration, validation, loading/error states, and verification.

Avoid generating the entire application in a single implementation step when the project has meaningful complexity.

## Platform-specific changes

Do not replace Lovable's underlying framework/build setup merely for architectural preference. Make platform-level changes only when the requirement clearly justifies them.
