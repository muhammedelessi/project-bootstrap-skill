# Project Bootstrap

A platform-agnostic Agent Skill for planning new software projects before large-scale implementation.

> **Version:** 1.0.0  
> **Status:** Public / reusable  
> **License:** MIT

Project Bootstrap turns a vague greenfield request into a deliberate architecture and phased build plan before the coding agent generates a large codebase.

It supports general web/mobile/backend projects and includes focused guidance for **React + TypeScript**, **Lovable**, **Flutter + Dart**, **backend/API systems**, and **Supabase**.

## Workflow

```text
Requirements
   ↓
Stack detection / selection
   ↓
Architecture & module boundaries
   ↓
Data model + Auth/Roles + Integrations
   ↓
Quality gates & critical flows
   ↓
Phased implementation plan
   ↓
Approval
   ↓
Incremental build + verification
```

The initial bootstrap phase is planning-first. Major implementation waits for approval unless the user has already explicitly approved the proposed architecture.

## Framework-aware, not framework-locked

The core workflow is general. The agent loads only the references relevant to the detected stack.

For Flutter, the skill follows current official Flutter architecture guidance: UI/data separation, Views + ViewModels, Repositories + Services, dependency injection, and `go_router` for ordinary routing. It does **not** force Riverpod, BLoC, or another state-management package on every project.

For Supabase, Project Bootstrap coordinates architecture and sequencing while delegating detailed schema, Auth, RLS, SQL, migrations, and performance work to a dedicated Supabase skill when available.

## Example requests

```text
Bootstrap a new SaaS app for three user roles. Plan the architecture before writing code.
```

```text
Start a Flutter application for field technicians with offline data and background sync.
```

```text
Plan a Lovable + Supabase customer portal with role-based access. Do not build until I approve the architecture.
```

```text
Design the initial architecture and phased implementation plan for this new backend API.
```

## Installation

### Lovable

Open your workspace and go to:

**Settings -> Skills -> Import -> GitHub**

Paste:

```text
https://github.com/muhammedelessi/project-bootstrap-skill
```

### Cursor

Copy or clone this repository into a supported project skill location such as:

```text
.agents/skills/project-bootstrap/
```

or:

```text
.cursor/skills/project-bootstrap/
```

### VS Code / GitHub Copilot

Use a supported project Agent Skills directory such as:

```text
.github/skills/project-bootstrap/
```

or:

```text
.agents/skills/project-bootstrap/
```

### Google Antigravity

Workspace scope:

```text
<project-root>/.agents/skills/project-bootstrap/
```

Global scope:

```text
~/.gemini/config/skills/project-bootstrap/
```

### Other Agent Skills-compatible tools

Place the complete skill directory in the tool's supported skills location so `SKILL.md` remains the entrypoint. Installation paths vary by agent, but the core skill follows the portable Agent Skills pattern.

## Repository structure

```text
.
├── SKILL.md
├── agents/
│   └── openai.yaml
├── references/
│   ├── architecture.md
│   ├── stack-detection.md
│   ├── react-typescript.md
│   ├── lovable-react.md
│   ├── flutter-dart.md
│   ├── backend-api.md
│   ├── supabase.md
│   ├── quality-gates.md
│   └── sources.md
├── CHANGELOG.md
├── CONTRIBUTING.md
└── LICENSE
```

## Design principle

This skill should prevent premature complexity, not create more of it. It favors explicit requirements, simple architecture, framework conventions, incremental delivery, and early verification.
