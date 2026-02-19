---
name: context-engineering
description: Guides context engineering practices for AI-assisted development in Cursor. Covers memory file hierarchies, knowledge document creation, token-efficient context management, progressive disclosure, context graphs, and structured documentation strategies.
---

# Context Engineering for Cursor

A guide to managing context so AI assistants produce accurate, project-specific code.

## ⚡️ Workflows

Select the guide relevant to your current task:

- **[Project Setup & Structure](refs/context-file-hierarchy.md)** — Where to put context files (`./docs/`, `architecture/`, `requirements/`).
- **[Create Knowledge Files](refs/knowledge-files.md)** — Workflow for documenting deep technical knowledge (niche libs, complex algos).
- **[Record Decisions (ADRs)](refs/architecture-decision-records.md)** — When and how to write Architecture Decision Records.
- **[Practical Recipes](refs/practical-workflows.md)** — Common tasks: starting projects, capturing session learnings, onboarding.
- **[Writing Guide](refs/writing-context-files.md)** — How to write effective context files that the AI can actually use.

## 🧠 Concepts & Optimization

- **[Progressive Disclosure](refs/progressive-disclosure.md)** — Structuring context as a graph to minimize token usage.
- **[Token Efficiency](refs/token-efficiency.md)** — Sizing guidelines and splitting strategies.
- **[Core Principles](refs/principles.md)** — The "Why", the Four Pillars, and measuring success.
- **[Prompt Templates](prompts/README.md)** — Reusable prompts for context tasks.
