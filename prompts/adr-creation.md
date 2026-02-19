---
name: adr-creation
description: Run after making a significant technical or architectural decision.
---

# ADR Creation

We just decided to [DECISION SUMMARY].

Create an Architecture Decision Record in docs/decisions/:

1. Determine the next ADR number by checking existing files in docs/decisions/
2. Create the file as [NUMBER]-[slug].md using the [template](~/.cursor/skills/context-engineering/templates/adr.md)
3. Fill in:
   - Context: what problem or situation prompted this decision
   - Decision: what we chose to do and how
   - Consequences: what becomes easier or harder as a result
4. Set the status to "accepted"
5. If this supersedes an existing ADR, update the old ADR's status
   to "superseded by [NEW NUMBER]"
6. Update any ./docs/ files that need to reflect this decision