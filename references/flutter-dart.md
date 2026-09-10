# Flutter + Dart Bootstrap

Follow current official Flutter architecture guidance for greenfield applications, adapting it to the app's actual complexity.

## Core architecture

Separate the app into a UI layer and a data layer.

Use these responsibilities by default:

- **Views**: render UI and forward user interactions.
- **ViewModels**: own UI logic and expose UI state/actions.
- **Repositories**: source of truth for application data and data-related business logic.
- **Services**: wrap external APIs, databases, files, device/platform services, and other low-level integrations.

Use an optional domain/use-case layer only when business logic is complex enough to justify it.

Do not put substantial business or data-access logic directly inside widgets.

## State management

Do not force Riverpod, BLoC, Provider, or another package across every project.

For a greenfield app, choose the lightest approach that fits the complexity and team conventions. Flutter's architecture guidance supports ViewModels and recommends dependency injection; `ChangeNotifier`/`Listenable` is a valid lightweight option, while other state-management packages are acceptable when justified.

If the project already chose a state-management approach, preserve it unless there is a concrete problem.

## Dependency injection

Prefer dependency injection over globally accessible service singletons. Keep dependencies explicit and replaceable for testing.

## Navigation

Use `go_router` for ordinary application routing unless the requirements call for a case it does not handle well.

## Organization

Use feature-oriented organization while preserving clear architectural responsibilities. A practical shape is:

```text
lib/
├── app/
│   ├── router/
│   └── app.dart
├── features/
│   ├── auth/
│   │   ├── presentation/
│   │   ├── view_models/
│   │   ├── repositories/
│   │   └── services/
│   └── orders/
│       ├── presentation/
│       ├── view_models/
│       ├── repositories/
│       └── services/
├── core/
│   ├── config/
│   ├── errors/
│   └── shared/
└── main.dart
```

Adapt this instead of treating it as a mandatory template.

## Testing

Plan tests along architectural boundaries:

- unit tests for services, repositories, and ViewModels
- widget tests for views and important interactions
- routing and dependency-injection tests where important
- integration/end-to-end tests for critical flows

Use fakes or test doubles through explicit interfaces/dependencies rather than making production code depend on global objects.
