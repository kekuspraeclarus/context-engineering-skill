---
name: new-project-bootstrap
description: Run when setting up context engineering for a new project.
---

# New Project Bootstrap

Analyse this codebase and create initial context files:

1. Create ./docs/ with:
   - `TECHNICAL-SPEC.md` - North star, deliverables, tech stack, open questions/decisions
   - `ARCHITECTURE.md` - Architecture overview, high-level directory tree, system boundaries.
   - `README.md` - Docs & ops overview. This describes the LLM context architecture, not anything to do with the project. Leave a note to keep these files [updated](context-maintenance.md) as the reader adds new things

   These docs' structures can be flexible - adapt it on a project-by-project basis. Include any sections that you think you'd find useful if you were reading this project for the first time.

2. For each major subdirectory, create .docs/architecture/[comprehensive-name].md files with:
   - Module purpose and responsibility
   - Design patterns used
   - Key abstractions

   Keep the architecture directory organised with a concise index file. Ensure that a fresh session can easily find what it's looking for

3. Identify any niche technologies that need [knowledge files](./knowledge-file-bootstrap.md) and list them for manual research.