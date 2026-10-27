---
type: Concept
title: dpBot Workspace Skills
description: >
  Workspace skills in dpBot — user-provided skills under the agent workspace.
tags:
  - nanobot
  - dpbot
  - skills
  - workspace
  - user-provided
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

# Workspace Skills

Workspace skills live under `<workspace>/skills/` in the agent workspace.
They are user-provided and can be customized or extended.

## Discovery and Invocation

Skills are discovered from:

1. Built-in skills under `nanobot/skills/`
2. Workspace skills under `<workspace>/skills/`
3. Plugin-provided skills from Agent Plugins

Skills can be invoked with `$skill-name` in conversation.

## Related

- [Skills Built-in](./skills-builtin.md) — Built-in skills
- [Skills Marketplace](./skills-marketplace.md) — Marketplace skills
- [WebUI Skills](./webui-skills.md) — Skills management in browser
- [Architecture](./architecture.md) — Source ownership
