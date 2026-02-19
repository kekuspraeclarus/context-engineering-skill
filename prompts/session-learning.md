---
name: session-learning
description: Run at the end of productive sessions to capture new knowledge.
---

# Session Learning

Review what we worked on this session. If during our conversation:

- You learned something new about the project
- I corrected you on a specific implementation detail
- I corrected source code you generated
- You struggled to find specific information
- You had to infer details about the project structure

...update the appropriate context files:

- Project-wide knowledge → ./docs/
- Subdomain-specific → ./docs/architecture/ in the relevant file
- Technical knowledge → docs/knowledge/
- Feature requirements → docs/requirements/
- Significant decisions → docs/decisions/ (create an ADR if we made a notable technical or architectural choice during this session)

Only add information that is relevant, was not previously documented, and should persist for future sessions.
Ask yourself "would  future me perform worse if they didn't know this?"