---
type: Concept
title: dpBot CLI WebUI
description: >
  CLI WebUI command in dpBot — WebUI management.
tags:
  - nanobot
  - dpbot
  - cli
  - webui
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

# CLI WebUI

The `nanobot webui` command manages the WebUI.

## Usage

```bash
nanobot webui [options]
```

## Options

| Option | Description |
|---|---|
| `--start` | Start the WebUI |
| `--stop` | Stop the WebUI |
| `--restart` | Restart the WebUI |
| `--status` | Show WebUI status |

## Related

- [CLI WebUI Reference](./cli-webui-reference.md) — Detailed WebUI commands
- [CLI Serve](./cli-serve-reference.md) — Serve command
- [CLI Agent](./cli-agent-reference.md) — Agent command
- [Architecture](./architecture.md) — Source ownership