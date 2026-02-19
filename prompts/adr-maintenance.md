---
name: adr-maintenance
description: Run periodically alongside context maintenance, or after major refactors.
---

# ADR Maintenance

Review all Architecture Decision Records in docs/decisions/:

1. Load all ADRs and their current statuses
2. For each accepted ADR, check whether the decision still holds by comparing against the actual codebase
3. Flag any ADRs where the codebase has drifted from the decision to ./ops/NOTES.md
4. Mark ADRs as deprecated if the relevant feature or pattern no longer exists
5. Identify decisions that have been informally superseded but lack a replacement ADR -- create one if appropriate
6. Verify that ./docs/ files are consistent with all accepted ADRs