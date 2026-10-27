---
type: Concept
title: dpBot Agent CLI Reference
description: >
  Agent CLI commands for dpBot — one-shot messages, interactive chat,
  session management, and terminal UI options.
tags:
  - nanobot
  - dpbot
  - cli
  - agent
  - terminal
  - session
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

# Agent CLI Reference

The dpBot agent CLI provides commands for sending messages and starting
interactive terminal chat.

## Global Options

| Option | Description |
|---|---|
| `--help` | Display help |
| `--version` | Show version |
| `--home <dir>` | Select config/workspace directory |
| `--config <path>` | Use specific config file |
| `--workspace <path>` | Override workspace |
| `--verbose` | Show verbose runtime output |

## One-Shot Commands

| Command | Description |
|---|---|
| `nanobot -m "Hello!"` | Send one message and exit |
| `nanobot --session <id>` | Use specific WebSocket session key |

## Interactive Commands

| Command | Description |
|---|---|
| `nanobot` | Start interactive terminal chat (TUI) |
| `nanobot agent` | Explicit alias for interactive chat |
| `nanobot --classic` | Use classic Python prompt instead of native TUI |
| `nanobot --theme auto|dark|light` | Terminal appearance |
| `nanobot --no-markdown` | Print plain text instead of Markdown |
| `nanobot --logs` | Show runtime logs while chatting |

The native TUI talks to the same local gateway as the WebUI. Streaming, tool progress, and WebSocket sessions share one protocol.

## Session Management

Inside the native TUI:

- `/sessions` switches saved conversations
- `/new-chat` starts another saved conversation
- `/context` explains the compacted summary and raw session suffix
- `/branch` forks a saved conversation from a completed reply
- `/diff` opens the latest turn's file changes as a unified diff

## Related

- [CLI Agent](./cli-agent.md) — CLI Agent overview
- [Gateway](./cli-gateway.md) — Gateway commands
- [WebUI](./cli-webui.md) — WebUI commands
- [Status](./cli-status.md) — Status commands
- [Channels](./cli-channels.md) — Channel commands
- [Plugins](./cli-plugins.md) — Plugin commands
- [Providers](./cli-providers.md) — Provider OAuth commands
- [Configuration](./configuration.md) — Config file and schema
- [WebUI](./webui-topics.md) — Browser workbench
- [Architecture](./architecture.md) — Source ownership and runtime flow
- [Automations](./automations-scheduled.md) — Cron, triggers, heartbeat