---
type: Concept
title: dpBot CLI Channels
description: >
  CLI Channels command in dpBot — channel management.
tags:
  - nanobot
  - dpbot
  - cli
  - channels
  - communication
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

# CLI Channels

## Overview

The `nanobot channels` command manages communication channels.

## Usage

```bash
nanobot channels [options]
```

## Options

| Option | Description |
|---|---|
| `--list` | List channels |
| `--add` | Add a channel |
| `--remove` | Remove a channel |
| `--enable` | Enable a channel |
| `--disable` | Disable a channel |

## Related

- [CLI Channels Reference](./cli-channels-reference.md) — Detailed channel commands
- [CLI Agent](./cli-agent-reference.md) — Agent command
- [CLI Gateway](./cli-gateway-reference.md) — Gateway command
- [Architecture](./architecture.md) — Source ownership