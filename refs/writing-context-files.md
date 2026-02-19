---
name: writing-context-files
description: Guidelines and examples for writing effective context files — focus on rationale, specificity, anti-patterns, and code references.
---

# Writing Effective Context Files

## Focus on the "Why"

Include rationale for decisions, not just the "what":

```markdown
## State Management
Use Zustand (not Redux).
Why: Smaller bundle, simpler API, sufficient for our scale.
Exception: If a feature requires time-travel debugging, discuss with the team first.
```

## Be Specific and Bounded

```markdown
## API Design
- REST with JSON responses
- Always return { data, error, meta } envelope
- Use HTTP status codes correctly (don't return 200 with error body)
- Rate limiting: 100 req/min per authenticated user
```

## Include Anti-Patterns

```markdown
## Don't
- Don't use `any` type in TypeScript (use `unknown` if truly dynamic)
- Don't import from barrel files in the same module
- Don't put business logic in API route handlers
```

## Reference Working Code

```markdown
## Patterns
For the canonical auth middleware implementation, see `src/middleware/auth.ts`
For the standard service class pattern, see `src/services/UserService.ts`
```
