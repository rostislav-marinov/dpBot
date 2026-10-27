---
type: Concept
title: dpBot WebUI CLI Reference
description: >
  WebUI CLI commands for dpBot — preparing, starting, and managing the
  browser workbench.
tags:
  - nanobot
  - dpbot
  - cli
  - webui
  - browser
  - workbench
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

# WebUI CLI Reference

`nanobot webui` prepares local WebUI settings, starts the gateway, and opens
the browser workbench.

## WebUI Commands

| Command | Description |
|---|---|
| `nanobot webui` | Prepare WebUI, start gateway, open browser |
| `nanobot webui --detach` | Start persistent gateway, open browser, return control |
| `nanobot webui --dev` | Start gateway and Vite dev server at `http://127.0.0.1:5173` |
| `nanobot webui --no-open` | Prepare and start without opening browser |
| `nanobot webui --no-dock` | Suppress macOS Dock icon |
| `nanobot webui --port <port>` | Set WebUI/WebSocket port |
| `nanobot webui --gateway-port <port>` | Override gateway health port |
| `nanobot webui --yes` | Apply safe localhost defaults without confirmation |

## First-Run Behavior

`nanobot webui` asks for one confirmation on a new installation, creates the
config/workspace, enables the local WebSocket channel, and generates a WebUI
bootstrap secret when one is missing.

First-run binds to `127.0.0.1` by default. Use manual configuration and a WebUI
password before exposing beyond localhost.

## Manual Configuration

```json
{
  "channels": {
    "websocket": {
      "enabled": true,
      "host": "127.0.0.1",
      "tokenIssueSecret": "your-webui-password",
      "websocketRequiresToken": true
    }
  }
}
```

## Related

- [CLI WebUI](./cli-webui.md) — CLI WebUI overview
- [Agent CLI](./cli-agent.md) — Agent commands
- [Gateway](./cli-gateway.md) — Gateway commands
- [WebUI](./webui-topics.md) — Browser workbench
- [Configuration](./configuration.md) — WebSocket channel settings
- [Security](./security.md) — Security boundaries