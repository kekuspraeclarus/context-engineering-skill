---
name: context-file-hierarchy
description: How to structure and place context files across a layered system — project, subdomain, and feature scopes.
---

# Context File Hierarchy in Cursor

Cursor uses a layered context system. Place information at the right level:

```
project-root/
  ├── docs/
  │   ├── architecture.md             # High-level architecture overview
  │   ├── decisions/                  # Architecture Decision Records
  │   │   ├── 0001-use-zustand-for-state.md
  │   │   ├── 0002-rest-over-graphql.md
  │   │   └── template.md            # ADR template
  │   ├── knowledge/                 # Deep technical knowledge files
  │   │   ├── ditto-policies.md      # Example: niche library reference
  │   │   └── auth-flow.md           # Example: complex subsystem docs
  │   ├── requirements/
  │   │   └── feature-x.prd.md       # Feature specifications
  │   └── architecture/
  |       └── section-a.md           # Directory/section/package docs
  └── ops/
      └──NOTES.md                    # Anything that needs the human's attention, but does not have a specific place
```

## Placement Principles

| Scope | Where | Examples |
|-------|-------|---------|
| Project-wide | `./docs/` at root | Architecture, tech stack, team conventions |
| Subdomain-specific | `./docs/architecture` | Frontend patterns, API design, infra rules |
| Feature-specific | `./docs/requirements/` | PRDs, user stories, acceptance criteria |
| Decision history | `docs/decisions/` | Tech choices, pattern adoptions, deprecations |
| Deep technical | `docs/knowledge/` referenced on demand | Niche library guides, algorithm references |