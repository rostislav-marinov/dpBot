---
type: Concept
title: dpBot CLI Gateway
description: >
  CLI Gateway command in dpBot — gateway management.
tags:
  - nanobot
  - dpbot
  - cli
  - gateway
  - management
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

# CLI Gateway

The `nanobot gateway` command manages the gateway service.

## Usage

```bash
nanobot gateway [options]
```

## Options

| Option | Description |
|---|---|
| `--start` | Start the gateway |
| `--stop` | Stop the gateway |
| `--restart` | Restart the gateway |
| `--status` | Show gateway status |

## Related

- [CLI Gateway Reference](./cli-gateway-reference.md) — Detailed gateway commands
- [CLI Agent](./cli-agent-reference.md) — Agent command
- [CLI Serve](./cli-serve-reference.md) — Serve command
- [Architecture](./architecture.md) — Source ownership