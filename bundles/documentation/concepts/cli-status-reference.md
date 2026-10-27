---
type: Concept
title: dpBot CLI Status Reference
description: >
  Status CLI commands for dpBot — checking installation, config, workspace,
  and provider/model readiness.
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
  - id: docs-cli-reference
    resource: /projects/dpBot/docs/cli-reference.md
    title: CLI Reference (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# CLI Status Reference

`nanobot status` summarizes the default config/workspace and checks
provider/model readiness.

## Status Commands

| Command | Description |
|---|---|
| `nanobot status` | Summarize default config/workspace and check provider/model readiness |
| `nanobot status --config <path>` | Check specific config |
| `nanobot status --workspace <path>` | Check with workspace override |

## Behavior

Status does not send a model request. On success, run `nanobot agent -m "Hello!"` to verify network access and credentials. On failure, follow the WebUI **Settings → Models** or `nanobot onboard --wizard` route.

## Related

- [CLI Agent](./cli-agent.md) — Agent commands
- [Gateway](./cli-gateway.md) — Gateway commands
- [Configuration](./configuration.md) — Config file and schema
- [Architecture](./architecture.md) — Source ownership and runtime flow
- [Troubleshooting](./troubleshooting.md) — Troubleshooting