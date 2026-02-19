---
name: principles
description: Core principles of context engineering - why we do it, the four pillars, and how to measure success.
---

# Context Engineering Principles

Context engineering is the deliberate practice of curating, structuring, and managing the knowledge available to AI assistants so they produce accurate, project-specific output.

## Core Principle

AI assistants excel at general problems but fail at project-specific tasks because they lack your context.
Context engineering closes that gap by systematically providing the "who, what, where, and why" of your codebase.

## The Four Pillars

1. **Project Architecture Knowledge** — class hierarchies, design patterns, naming conventions.
2. **Product Requirements Documentation** — user stories, acceptance criteria, business logic.
3. **Deep Technical Knowledge** — niche libraries, recent API changes, complex algorithms.
4. **Architecture Decision Records** — key choices, trade-offs, alternatives rejected.

## Four Pillars of Context Management

1. **Write** - Capture important information to persistent files.
2. **Select** - Load only the context relevant to the current task.
3. **Compress** - Summarise and filter to stay within token budgets.
4. **Isolate** - Separate context domains to prevent cross-contamination.