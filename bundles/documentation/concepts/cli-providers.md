---
type: Concept
title: dpBot CLI Providers
description: >
  CLI Providers command in dpBot — provider management.
tags:
  - nanobot
  - dpbot
  - cli
  - providers
  - model
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

# CLI Providers

The `nanobot providers` command manages model providers.

## Usage

```bash
nanobot providers [options]
```

## Options

| Option | Description |
|---|---|
| `--list` | List providers |
| `--add` | Add a provider |
| `--remove` | Remove a provider |
| `--switch` | Switch provider |

## Related

- [CLI Providers Reference](./cli-providers-reference.md) — Detailed provider commands
- [CLI Agent](./cli-agent-reference.md) — Agent command
- [Gateway](./cli-gateway-reference.md) — Gateway command
- [Architecture](./architecture.md) — Source ownership