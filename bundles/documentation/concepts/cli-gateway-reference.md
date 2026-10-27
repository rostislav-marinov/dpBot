---
type: Concept
title: dpBot Gateway CLI Reference
description: >
  Gateway CLI commands for dpBot — starting, stopping, managing, and
  inspecting the gateway process.
tags:
  - nanobot
  - dpbot
  - cli
  - gateway
  - service
  - management
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

# Gateway CLI Reference

`nanobot gateway` starts enabled chat channels, WebUI/WebSocket, cron-backed
system jobs, Dream, heartbeat, and the health endpoint.

## Starting the Gateway

| Command | Description |
|---|---|
| `nanobot gateway` | Start gateway in foreground |
| `nanobot gateway --verbose` | Show verbose runtime output |
| `nanobot gateway --port <port>` | Override health endpoint port |
| `nanobot gateway --background` | Start as background process |
| `nanobot gateway --workspace <path>` | Override workspace |
| `nanobot gateway --config <path>` | Use specific config file |

## Status and Logs

| Command | Description |
|---|---|
| `nanobot gateway status` | Show PID, mode, client count, state, logs |
| `nanobot gateway logs` | Follow background gateway logs |
| `nanobot gateway logs --no-follow` | Print recent logs and exit |

## Restart and Stop

| Command | Description |
|---|---|
| `nanobot gateway restart` | Restart recorded background gateway |
| `nanobot gateway stop` | Stop recorded background gateway |

On Windows, `gateway stop` waits up to `--timeout` seconds (default: 20) for the gateway to stop normally.

## Service Management

| Command | Description |
|---|---|
| `nanobot gateway install-service` | Install systemd user service or macOS LaunchAgent |
| `nanobot gateway install-service --dry-run` | Preview the generated service file |
| `nanobot gateway uninstall-service` | Remove installed system service |

## Health Endpoint

Default health endpoint: `http://127.0.0.1:18790/health`

The bundled WebUI is served by the WebSocket channel on port `8765` by default,
not by the gateway health endpoint.

## Related

- [CLI Gateway](./cli-gateway.md) — CLI Gateway overview
- [Agent CLI](./cli-agent.md) — Agent commands
- [WebUI](./cli-webui.md) — WebUI commands
- [Configuration](./configuration.md) — Gateway settings
- [Architecture](./architecture.md) — Gateway runtime
- [Automations](./automations-scheduled.md) — System jobs