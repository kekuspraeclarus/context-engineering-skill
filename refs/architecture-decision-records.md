---
name: architecture-decision-records
description: Full guide to Architecture Decision Records — when to write them, template, numbering, lifecycle, and relationship to context files.
---

# Architecture Decision Records

ADRs capture the reasoning behind significant project decisions at the point they are made.
Unlike rules files (which reflect the *current* state of conventions), ADRs preserve the *historical context* -- what was decided, why, and what alternatives were rejected. The key here is "why" - it will help you stop reverting changes back to undesirable states when the undesirable state seems to make more sense at a first glance.

## When to Write an ADR

Write an ADR when:

- Choosing or switching a framework, library, or major dependency
- Changing a core architectural pattern (e.g. moving from REST to GraphQL)
- Adopting or dropping a convention that affects the whole team
- Deviating from an established pattern for a specific reason
- Making a trade-off that future developers will question

If someone might later ask "why did we do it this way?", the answer belongs in an ADR.

## ADR Template

Use a lightweight, consistent [structure](~/.cursor/skills/context-engineering/templates/adr.md)

Numbers are never reused. If a decision is superseded, the original keeps its number and its status is updated to point to the replacement.

## ADR Lifecycle

```
proposed → accepted → deprecated
                    → superseded by XXXX
```

- **Proposed** - Under discussion, not yet agreed upon
- **Accepted** - Agreed and in effect
- **Deprecated** - No longer relevant (e.g. the feature was removed)
- **Superseded** - Replaced by a newer decision (link to the new ADR)

When an ADR is superseded or deprecated, update the corresponding `./docs/` files to reflect the new convention.
ADRs themselves are append-only -- never delete or rewrite the original reasoning.