---
name: progressive-disclosure
description: Structuring large knowledge domains as traversable graphs with progressive disclosure so agents load only the context that directly informs the current task.
---

# Progressive Disclosure & Context Graphs

A single context file works for a single concern.
When a domain spans many interconnected concepts — architecture, patterns, policies, techniques — a flat collection of files forces you to either load too much or miss important links.
Context graphs solve this.

## The Problem with Flat Context

Loading an entire knowledge domain into context wastes tokens and dilutes attention.
The agent receives information about position sizing when the task is about risk management, or reads attachment theory when the question is about active listening.
Every irrelevant paragraph competes with the useful ones.

## Progressive Disclosure

Structure context so the agent can make decisions about what to load *before* reading full files:

```
index → descriptions → links → sections → full content
```

Most routing decisions happen before reading a single full file. Each layer reveals just enough to decide whether to go deeper:

1. **Index file** — lists what exists, grouped by sub-topic, with one-line summaries
2. **YAML frontmatter** — every file has a `description` field the agent can scan without reading the body
3. **Wikilinks in prose** — links embedded in sentences carry meaning ("use [risk-management]({link}) when position size exceeds threshold") so the agent follows relevant paths and skips the rest
4. **Sections within files** — each file covers one complete concept; the agent reads only the sections it needs
5. **Full content** — loaded only when the agent is confident the file is relevant

## Context Graphs

A context graph is a network of focused context files connected by meaningful references.
Each file is one complete concept, technique, decision, or piece of knowledge.
Links between them create a traversable graph the agent navigates based on the current task.

### Structure

```
docs/knowledge/
  ├── index.md                    # Entry point — landscape + navigation
  ├── topic-a/
  │   ├── _moc.md                 # Map of content for this cluster
  │   ├── concept-one.md
  │   ├── concept-two.md
  │   └── concept-three.md
  └── topic-b/
      ├── _moc.md
      ├── technique-one.md
      └── technique-two.md
```

### The Index File

The index is not a lookup table — it is an entry point that directs attention.
The agent reads it, understands the landscape, and follows only the links that matter for the current conversation.

```markdown
# Domain Name

One-paragraph summary of what this knowledge domain covers.

## Topic Clusters

- [topic-a/_moc]({link}) — one-line description of what this cluster covers
- [topic-b/_moc]({link}) — one-line description of what this cluster covers

## Cross-Cutting Concerns

- [concept-that-spans-topics]({link}) — why it matters across boundaries
```

### Maps of Content (MOCs)

When a topic cluster grows beyond 5-7 files, add a MOC that organises the cluster.
MOCs are intermediate navigation — more detail than the index, less than reading every file.

You do not need a MOC for small directories or clusters. It just adds unnecessary complexity.

```markdown
---
description: Risk management strategies — position sizing, stop losses, portfolio correlation.
---

# Risk Management

## Core Techniques
- [position-sizing]({link}) — Kelly criterion and fractional approaches
- [stop-loss-strategies]({link}) — trailing, time-based, volatility-adjusted

## Supporting Concepts
- [portfolio-correlation]({link}) — why diversification math breaks during crises
```

### Individual Files

Each file covers one complete concept. Keep them focused and self-contained:

```markdown
---
description: Kelly criterion for optimal position sizing given edge and odds.
---

# Position Sizing

[content about position sizing]

When calculating size, account for [portfolio-correlation]({link}) effects.
For stop placement that complements sizing, see [stop-loss-strategies]({link}).
```

The wikilinks read as prose. They tell the agent *when and why* to follow them, not just that a connection exists.

## Applying This to Context Engineering

When structuring project knowledge:

1. **Split by decision boundary** — each file should cover one concept the agent can decide to load or skip independently
2. **Write descriptions that enable skipping** — if the YAML description tells the agent enough to know "this is not relevant right now", the file has done its job without being read
3. **Embed links in context** — don't list links at the bottom; weave them into the prose where they carry meaning about *when* to follow them
4. **Use MOCs at ~7 files** — below that, the index is sufficient; above that, the agent needs intermediate navigation
5. **Measure by what is NOT loaded** — a well-structured graph is proven by the files the agent correctly ignores, not the ones it reads

## When to Use This Pattern

- Knowledge domains with more than ~5 interconnected files
- Context that serves multiple different task types (the same domain, different entry points)
- Domains where loading everything would exceed ~30KB of context
- Situations where the agent repeatedly loads irrelevant context alongside relevant content

For smaller, focused knowledge areas, a single well-structured file with clear sections is still the right choice. Don't over-engineer context that fits comfortably in one document.