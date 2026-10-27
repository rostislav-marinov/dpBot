---
type: Concept
title: dpBot Skills Marketplace
description: >
  Skills Marketplace in dpBot — discover and install skills from ClawHub.
tags:
  - nanobot
  - dpbot
  - skills
  - marketplace
  - clawhub
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:30:00Z
sources:
  - id: docs-concepts
    resource: /projects/dpBot/docs/concepts.md
    title: Concepts (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# Skills Marketplace

The Skills Marketplace allows discovering and installing skills from ClawHub,
the public skill registry.

## Discovery and Invocation

Skills are discovered from:

1. Built-in skills under `nanobot/skills/`
2. Workspace skills under `<workspace>/skills/`
3. Plugin-provided skills from Agent Plugins

## Installing from ClawHub

Use the `clawhub` skill to search and install skills:

- `clawhub search <query>` — Search for skills
- `clawhub install <skill-name>` — Install a skill

## Related

- [Built-in Skills](./skills-builtin.md) — Bundled skills
- [Workspace Skills](./workspace-skills.md) — User-provided skills
- [WebUI Skills](./webui-skills.md) — Skills management in browser
- [Architecture](./architecture.md) — Source ownership
