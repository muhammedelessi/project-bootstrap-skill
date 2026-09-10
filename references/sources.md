# Sources and Maintenance

Use current official documentation when framework behavior or recommended architecture may have changed.

## Flutter

- Architecture overview: https://docs.flutter.dev/app-architecture
- Architecture guide: https://docs.flutter.dev/app-architecture/guide
- Architecture recommendations: https://docs.flutter.dev/app-architecture/recommendations

The Flutter guidance currently strongly recommends clear UI/data layers, repositories and services, Views/ViewModels, dependency injection, and testing architectural components. It recommends `go_router` for most app navigation and treats specific state-management mechanisms as context-dependent.

## React

- Thinking in React: https://react.dev/learn/thinking-in-react
- Choosing the State Structure: https://react.dev/learn/choosing-the-state-structure

Favor minimal, non-duplicated state and clear ownership.

## Agent Skills portability

- Open standard information: https://agentskills.io
- Cursor Skills docs: https://cursor.com/docs/context/skills
- VS Code Agent Skills: https://code.visualstudio.com/docs/agent-customization/agent-skills
- Google Antigravity Skills: https://antigravity.google/docs/skills/

## Supabase

- Official Supabase docs: https://supabase.com/docs
- Official Supabase Agent Skills repository: https://github.com/supabase/agent-skills

When detailed Supabase guidance is needed, prefer the current official docs or a synchronized dedicated Supabase skill rather than duplicating fast-changing platform rules here.
