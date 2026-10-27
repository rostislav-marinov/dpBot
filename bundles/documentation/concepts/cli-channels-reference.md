---
type: Concept
title: dpBot Channel CLI Reference
description: >
  Channel CLI commands for dpBot — connecting, managing, and inspecting
  chat platform channels.
tags:
  - nanobot
  - dpbot
  - cli
  - channels
  - chat
  - platform
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

# Channel CLI Reference

| Command | Description |
|---|---|
| `nanobot channels status` | Show configured channel status |
| `nanobot channels login <channel>` | Run interactive login for supported channels |
| `nanobot channels login <channel> --force` | Re-authenticate |
| `nanobot channels login <channel> --config <path>` | Use specific config file |
| `nanobot plugins list` | Show plugin/channel enabled state |
| `nanobot plugins enable <name>` | Install missing support and enable feature/channel |
| `nanobot plugins disable <channel>` | Turn off channel without deleting settings |

## Related

- [CLI Channels](./cli-channels.md) — CLI Channels overview
- [Agent CLI](./cli-agent.md) — Agent commands
- [Gateway](./cli-gateway.md) — Gateway commands
- [Configuration](./configuration.md) — Channel settings
- [WebUI](./webui-topics.md) — Channel management in browser
- [Architecture](./architecture.md) — Channel discovery