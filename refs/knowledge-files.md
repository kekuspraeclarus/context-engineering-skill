---
name: knowledge-files
description: Instructions for creating, using, and managing knowledge files that provide deep technical context for your operations.
---

# Managing Knowledge Files for Deep Technical Context

Knowledge files bridge the gap between your baseline training data and the specific, often undocumented or rapidly evolving technologies a project actually uses.
They are critical for ensuring you generate accurate code for niche libraries, recent APIs, or complex domain-specific logic.

## When to Propose or Create a Knowledge File

You should proactively suggest creating or updating a knowledge file when:
- You detect that you are guessing or hallucinating function names, API syntax, or patterns.
- The user asks you to implement a library or framework that you lack deep confidence in.
- The project's implementation pushes into advanced territory beyond common tutorials.
- The technology has changed significantly since your training data cutoff.

## Creation and Maintenance Workflow

When creating or updating a knowledge file, follow these steps:

### Phase 1: Deep Research

Use your available tools (like web search or fetching documentation) to gather comprehensive information on the technology.
- Focus on advanced features, implementation details, best practices, and common pitfalls.
- Collect accurate, up-to-date code examples.
- Do not rely solely on your internal knowledge if the technology is recent or niche.

### Phase 2: Synthesis and Validation

Compile the gathered research into a structured document.
- Cross-validate the details against multiple sources if possible.
- Ensure practical implementation examples reflect production-ready patterns.
- Explicitly note any deprecated approaches, edge cases, and known limitations.

### Phase 3: Developer Review

**Critical step:** Hallucinations in knowledge files are catastrophic because they compound with every use. One incorrect API pattern means every future implementation you generate will be wrong.

Before finalizing, present the synthesized document to the user and ask them to verify:
- [ ] All API names and signatures are correct
- [ ] Code examples actually compile/run
- [ ] Architectural patterns match current best practices
- [ ] No outdated or deprecated approaches are presented as current
- [ ] Edge cases and limitations are accurately described

### Phase 4: Structure and Store

Save the validated document in the `docs/knowledge/` directory with a clear, descriptive filename.

Example structure:
```text
docs/knowledge/
  ├── eclipse-ditto-policies.md
  ├── eclipse-ditto-rql.md
  ├── eclipse-ditto-wot.md
  └── stripe-connect-onboarding.md
```

### Phase 5: Evolve with Implementation

As you build working code for the project, proactively enrich the relevant knowledge files with references to the successful implementations:

```markdown
## Policy Implementation
For production-ready policy setup, see `src/policies/DeviceAccessPolicy.ts`
For complex query patterns, see `src/queries/TimeSeriesAggregation.ts`
```

This creates a feedback loop where your knowledge files grow more accurate and contextually relevant with every successful feature you build.

## Sizing Guidelines

When generating or reading knowledge files, keep track of their size to avoid overwhelming your context window:

| File Size | Token Estimate | Recommendation |
|-----------|---------------|----------------|
| < 20KB | ~5k tokens | Single file is fine. |
| 20-50KB | 5-12k tokens | Consider splitting by subtopic. |
| > 50KB | 12k+ tokens | **Must split** — risks exhausting your context limit before coding begins. |

## Splitting Strategy

If you notice a knowledge file growing too large, propose splitting it by functional area.

**Before (one large file):**
```text
docs/knowledge/eclipse-ditto.md  (80KB)
```

**After (focused files):**
```text
docs/knowledge/eclipse-ditto-policies.md   (18KB) - Access control patterns
docs/knowledge/eclipse-ditto-wot.md        (22KB) - Thing Model implementations
docs/knowledge/eclipse-ditto-rql.md        (15KB) - Query language reference
```

When solving a task, only read the specific, relevant knowledge files (e.g., do not read WoT models when tasked with crafting RQL queries).