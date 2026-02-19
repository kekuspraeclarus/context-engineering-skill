---
name: token-efficiency
description: Managing context token budgets — sizing guidelines, splitting strategies, and creating knowledge files via research.
---

# Token Efficiency

Context competes for the same token budget as your conversation. Manage it carefully:

- Keep individual context files under 500 lines
- Split large knowledge documents by topic (e.g. `auth-policies.md`, `query-language.md`, `thing-models.md`)
- Use wikilinks references to trigger loading context on conditionally rather than stuffing everything into large files
- Remove obsolete information promptly
- Prefer concise, structured formats over prose

## When Context Gets Too Large

If a knowledge file exceeds ~50KB (~12k tokens):

1. Split by subtopic into separate files
2. Create an index file listing what each sub-file covers
3. Reference only the relevant sub-file when needed

## Structuring Large Knowledge Domains

When a domain spans many interconnected concepts, splitting by subtopic alone is not enough — the agent still loads files it does not need. Use progressive disclosure and skill graphs to let the agent navigate to only the relevant pieces. See [progressive-disclosure.md](progressive-disclosure.md) for the full pattern.

## Creating Knowledge Files via Research

For niche technologies the AI may hallucinate about:

1. **Research phase** - Use external research tools to generate comprehensive technical documentation
2. **Validation phase** - Have a domain expert review for accuracy (hallucinations in knowledge files compound with every use)
3. **Storage** - Place in `docs/knowledge/` with clear, descriptive filenames
4. **Reference** - Pull into context using wikilinks when relevant
5. **Evolve** - Enrich with references to working code as implementations mature

See [knowledge-files.md](knowledge-files.md) for the detailed workflow.
