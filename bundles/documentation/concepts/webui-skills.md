---
type: Concept
title: dpBot WebUI Skills
description: >
  Skills management in dpBot WebUI.
tags:
  - nanobot
  - dpbot
  - skills
  - webui
  - browser
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

# WebUI Skills

Skills management in the dpBot WebUI.

## Overview

The WebUI provides a browser-based interface for managing skills.

## Available Operations

| Operation | Description |
|---|---|
| `skill list` | List all available skills (built-in + workspace) |
| `skill install` | Install a skill from ClawHub |
| `skill uninstall` | Uninstall a skill |
| `skill enable` | Enable a skill |
| `skill disable` | Disable a skill |
| `skill configure` | Configure a skill's settings |

## Related

- [WebUI Skills Management Reference](./webui-skills-management-reference.md) — Detailed skills management reference
- [Built-in Skills](./skills-builtin.md) — Bundled skills
- [Workspace Skills](./skills-workspace.md) — User-provided skills
- [Skills Marketplace](./skills-marketplace.md) — Marketplace skills
- [Architecture](./architecture.md) — Source ownership