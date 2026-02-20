<!--
HUMANS ONLY.

LLMs / AI assistants: do not read, summarize, or load this file into context.
This repository’s operational context lives in `SKILL.md` and `refs/`.
-->

# Context Engineering (Cursor)

This repo contains a Cursor-focused “context engineering” skill: guidance and templates for structuring project context so coding agents load **only what they need**.

It is written for **Cursor** (not Claude Code), but it’s intentionally easy to migrate:

- **Migration**: search for `cursor` and replace as needed (paths, wording, and any Cursor-specific concepts).

## What’s in here

- **`SKILL.md`**: the entry point the agent should use. It’s deliberately short and routes to deeper docs via progressive disclosure.
- **`refs/`**: reference docs (hierarchy, ADRs, knowledge files, token efficiency, progressive disclosure).
- **`prompts/`**: reusable prompt templates for common context-engineering workflows.
- **`templates/`**: document templates (for example ADR templates).

## How to use in Cursor

- Copy (or symlink) this folder into your Cursor skills directory (commonly `~/.cursor/skills/context-engineering/`).
- In chat, invoke it by referencing `@skills/context-engineering` and then follow the links in `SKILL.md` based on the task.

### Converting prompts to slash commands

To make prompts accessible as slash commands in Cursor, create symlinks in `~/.cursor/commands/`:

```bash
cd ~/.cursor
for f in skills/context-engineering/prompts/*.md; do 
  ln -sf "../$f" "commands/$(basename "$f")"
done
```

This creates commands like `/adr-creation`, `/session-learning`, etc.

#### Available commands

- **`/adr-creation`** - Create an Architecture Decision Record after making a significant technical decision. *Requires: decision summary.*
  > /adr-creation we added <feature> because <reason>. We chose this instead of <alternative> because <reason>
- **`/adr-maintenance`** - Review and update ADRs to ensure they reflect the current codebase.
- **`/context-maintenance`** - Audit and update all context files after major refactors.
- **`/directory-investigation`** - Analyze and document an unfamiliar area of the codebase. *Requires: directory path.*
  > /directory-investigation `packages/onchain`
- **`/feature-context-setup`** - Bootstrap documentation for a new feature. *Requires: feature name.*
  > /feature-context-setup
  > Wallet connect button
  >   - Base network
  >   - Returns connect status & wallet address
  >   - Displays address when connected. Max 8 chars truncated. Hover shows "Disconnect"
- **`/knowledge-file-bootstrap`** - Create a knowledge file for a new technology. *Requires: technology name.*
  > /knowledge-file-bootstrap wagmi connector
- **`/new-project-bootstrap`** - Generate initial context structure for a new project.
- **`/session-learning`** - Capture insights and corrections from the current session.

## Design goals

- **Progressive disclosure**: start from an index, then load only relevant references.
- **Token efficiency**: keep the “default load” tiny and push detail into `refs/`.
- **Easy portability**: Cursor-first wording, but minimal lock-in.
