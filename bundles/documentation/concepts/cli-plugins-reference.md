---
type: Concept
title: dpBot Plugin CLI Reference
description: >
  Plugin CLI commands for dpBot — managing optional features and runtime
  support packages.
tags:
  - nanobot
  - dpbot
  - cli
  - plugins
  - features
  - optional
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

# Plugin CLI Reference

The `plugins` command manages nanobot runtime support packages, not the
user-invokable tools shown in WebUI Apps.

## Optional Features

| Feature | What it enables |
|---|---|
| `api` | Dependencies for OpenAI-compatible `nanobot serve` |
| `azure` | Azure identity support for Azure-hosted models |
| `bedrock` | AWS Bedrock model provider support |
| `langfuse` | Langfuse tracing for OpenAI-compatible providers and Codex OAuth |
| `olostep` | Olostep web search provider support |
| `telegram`, `slack`, etc. | Connector package and saved channel enablement |

## Plugin Commands

| Command | Description |
|---|---|
| `nanobot plugins list` | Show available channels and optional capabilities |
| `nanobot plugins enable <name>` | Install missing support and enable feature/channel |
| `nanobot plugins enable <name> --logs` | Show package install logs while enabling |
| `nanobot plugins disable <channel>` | Turn off channel without deleting settings |
| `nanobot plugins list --config <path>` | Read a specific config file |
| `nanobot plugins enable <name> --config <path>` | Update a specific config file |
| `nanobot plugins disable <channel> --config <path>` | Turn off a channel in a specific config file |

Document and PDF reading are included in the standard installation. The old
`nanobot plugins enable documents` and `nanobot plugins enable pdf` commands
remain accepted as no-op compatibility aliases.

## Related

- [CLI Plugins](./cli-plugins.md) — CLI Plugins overview
- [Agent CLI](./cli-agent.md) — Agent commands
- [Gateway](./cli-gateway.md) — Gateway commands
- [Channels](./cli-channels.md) — Channel commands
- [WebUI](./webui-topics.md) — Apps management in browser
- [Configuration](./configuration.md) — Config file and schema