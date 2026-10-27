---
type: Concept
title: dpBot CLI Serve
description: >
  CLI Serve command in dpBot — serve the WebUI.
tags:
  - nanobot
  - dpbot
  - cli
  - serve
  - webui
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

# CLI Serve

## Overview

The `nanobot serve` command starts the WebUI server.

## Usage

```bash
nanobot serve [options]
```

## Options

| Option | Description |
|---|---|
| `--port` | Port number |
| `--host` | Host address |
| `--config` | Config file path |

## Related

- [CLI Serve Reference](./cli-serve-reference.md) — Detailed serve commands
- [CLI Agent](./cli-agent-reference.md) — Agent command
- [CLI Gateway](./cli-gateway-reference.md) — Gateway command
- [Architecture](./architecture.md) — Source ownership