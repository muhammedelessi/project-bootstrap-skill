# React + TypeScript Bootstrap

Use this guidance for React/TypeScript applications unless a framework such as Next.js imposes stronger conventions.

## Components and features

Design component boundaries around user-visible responsibilities and business capabilities. Keep page/screen components focused on composition. Extract reusable components only when reuse or complexity is real.

Prefer feature-oriented modules for substantial applications. Keep shared UI primitives, cross-cutting hooks, configuration, and infrastructure intentionally small.

## State

Keep state minimal and non-duplicated.

- Keep transient UI state close to where it is used.
- Lift state only when multiple components genuinely share ownership.
- Derive values instead of storing duplicates.
- Avoid global state by default.
- Distinguish server/remote data from local interaction state.

Do not add a state-management library until built-in React state/context and the chosen data-fetching approach are demonstrably insufficient.

## TypeScript boundaries

Use explicit types at API, persistence, form, and integration boundaries. Avoid using `any` to silence uncertainty. Validate untrusted runtime data even when TypeScript types exist.

## Data access

Do not scatter direct API/database calls throughout presentation components. Centralize access behind feature-level clients, services, repositories, or server actions appropriate to the chosen framework.

## Routing and forms

Choose routing and form libraries only after the framework and requirements are known. Preserve framework-native patterns when they are sufficient.

## Testing

At minimum, test critical business logic and critical user flows. Prefer behavior-focused component tests over tests that mirror implementation details.
