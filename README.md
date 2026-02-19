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

## Design goals

- **Progressive disclosure**: start from an index, then load only relevant references.
- **Token efficiency**: keep the “default load” tiny and push detail into `refs/`.
- **Easy portability**: Cursor-first wording, but minimal lock-in.