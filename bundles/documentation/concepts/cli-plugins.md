---
type: Concept
title: dpBot CLI Plugins
description: >
  CLI Plugins command in dpBot — plugin management.
tags:
  - nanobot
  - dpbot
  - cli
  - plugins
  - extensions
  - optional
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

# CLI Plugins

The `nanobot plugins` command manages agent plugins.

## Usage

```bash
nanobot plugins [options]
```

## Options

| Option | Description |
|---|---|
| `--list` | List plugins |
| `--install` | Install a plugin |
| `--uninstall` | Uninstall a plugin |
| `--enable` | Enable a plugin |
| `--disable` | Disable a plugin |

## Related

- [CLI Plugins Reference](./cli-plugins-reference.md) — Detailed plugin commands
- [CLI Agent](./cli-agent-reference.md) — Agent command
- [Gateway](./cli-gateway-reference.md) — Gateway command
- [Architecture](./architecture.md) — Source ownership