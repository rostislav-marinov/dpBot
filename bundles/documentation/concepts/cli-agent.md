---
type: Concept
title: dpBot CLI Agent
description: >
  CLI Agent command in dpBot — agent execution from terminal.
tags:
  - nanobot
  - dpbot
  - cli
  - agent
  - terminal
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

# CLI Agent

The `nanobot agent` command runs the agent from the terminal.

## Usage

```bash
nanobot agent [options]
```

## Options

| Option | Description |
|---|---|
| `--workspace` | Workspace path |
| `--config` | Config file path |
| `--model` | Model preset |

## Related

- [CLI Agent Reference](./cli-agent-reference.md) — Detailed CLI Agent commands
- [CLI Gateway](./cli-gateway-reference.md) — Gateway command
- [CLI Serve](./cli-serve-reference.md) — Serve command
- [Architecture](./architecture.md) — Source ownership