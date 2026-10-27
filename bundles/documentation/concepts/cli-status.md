---
type: Concept
title: dpBot CLI Status
description: >
  CLI Status command in dpBot — status checking.
tags:
  - nanobot
  - dpbot
  - cli
  - status
  - diagnostics
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

# CLI Status

The `nanobot status` command shows the current status.

## Usage

```bash
nanobot status [options]
```

## Options

| Option | Description |
|---|---|
| `--workspace` | Workspace path |
| `--config` | Config file path |
| `--json` | JSON output |

## Related

- [CLI Status Reference](./cli-status-reference.md) — Detailed status commands
- [CLI Agent](./cli-agent-reference.md) — Agent command
- [Gateway](./cli-gateway-reference.md) — Gateway command
- [Architecture](./architecture.md) — Source ownership