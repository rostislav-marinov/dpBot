---
type: Configuration
title: dpBot Configuration
description: >
  Full configuration reference for the dpBot nanobot fork, including
  config schema, model presets, tools, MCP, and security settings.
tags:
  - nanobot
  - configuration
  - config
  - mcp
  - security
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:10:00Z
sources:
  - id: docs-configuration
    resource: /projects/dpBot/docs/configuration.md
    title: Configuration (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# Configuration

Config file: `~/.nanobot/config.json`

## Config vs Workspace

| Path | Meaning |
|---|---|
| `~/.nanobot/config.json` | Instance configuration: providers, model defaults, channels, tools, gateway, API, and runtime options |
| `~/.nanobot/workspace/` | Agent workspace: memory, heartbeat tasks, cron jobs, skills, and generated artifacts |
| `~/.nanobot/sessions/<workspace-id>/` | Session history stored outside the agent-accessible workspace |

## Config Format

`config.json` accepts both camelCase and snake_case keys. The docs use
camelCase because nanobot writes config back to disk with camelCase aliases.

## Key Sections

### Providers

Provider metadata is centralized in `nanobot/providers/registry.py`.
Configuration fields live in `nanobot/config/schema.py`.

Provider selection uses:
1. Explicit `agents.defaults.provider` or preset provider.
2. Provider registry keywords.
3. API key prefixes and API base URL hints.
4. Local provider fallback when `apiBase` is configured.
5. Gateway fallback for providers that can route many model families.

### Model Presets

Named presets in `modelPresets`. The active preset is selected by
`agents.defaults.modelPreset`.

### MCP

MCP servers are configured under `tools.mcpServers.<name>`. Each entry
specifies a command, args, and optional env.

### Security

- `tools.restrictToWorkspace` — restrict file/shell tools to the workspace.
- `tools.exec.sandbox` — sandbox shell execution.
- `tools.ssrfWhitelist` — allowlist for outbound HTTP requests.
- `channels.*.allowFrom` — restrict which chat-app senders may interact.

### Environment Variables for Secrets

Any string value in `config.json` can use `${VAR_NAME}` references that
are resolved from environment variables at startup.

## Related

- [Architecture](./architecture.md) — Source ownership and runtime flow.
- [Memory](./memory.md) — Memory and Dream configuration.
- [MCP](./mcp.md) — Model Context Protocol servers.