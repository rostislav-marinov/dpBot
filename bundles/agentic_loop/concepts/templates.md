---
type: Component
title: dpBot Templates (Implementation)
description: >
  Template system in dpBot — prompt templates, system prompts, and template
  rendering for agent turns.
tags:
  - nanobot
  - agentic-loop
  - templates
  - prompts
  - system-prompts
  - runtime
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T20:00:00Z
sources:
  - id: dpbot-templates
    resource: /projects/dpBot/nanobot/templates
    title: Templates (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
---

# Templates (Implementation)

The template system in dpBot provides prompt templates and system prompts
for agent turns.

## Template Directory

Templates live under `nanobot/templates/` in the source tree:

- System prompt templates
- Skill prompt templates
- Tool prompt templates
- Channel-specific templates

## Template Rendering

Templates are rendered with context variables:

- Session context
- Workspace context
- User profile
- Skill instructions
- Tool schemas

## Bootstrap Identity Files

Bootstrap identity files are part of the template system:

- `SOUL.md` — The bot's long-term voice and communication style
- `USER.md` — Stable knowledge about the user
- Templates under `nanobot/templates/`

## Related

- [AgentLoop](./agentloop.md)
- [Core Flow](./core-flow.md)
- [Memory and Sessions](./memory-sessions.md)
- [dpBot Documentation bundle](../documentation/index.md)
