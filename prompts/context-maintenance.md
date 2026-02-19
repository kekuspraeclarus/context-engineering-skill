---
name: context-maintenance
description: Run after major refactors.
---

# Context Maintenance

Review all context and rules files in this project:

1. Load the contents of ./docs/
2. For each file, compare documented patterns against actual codebase implementation
3. Identify outdated, incorrect, or missing information
4. Remove obsolete entries
5. Consolidate duplicates
6. Fill gaps with current patterns
7. Review docs/decisions/ for ADRs that should be deprecated or
   superseded based on how the codebase has evolved
8. Ensure accepted ADRs are consistent with current rules files

Focus on accuracy and relevance. Remove anything that no longer reflects the codebase.