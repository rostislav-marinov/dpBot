---
type: Concept
title: dpBot MCP Config
description: >
  MCP configuration in dpBot — server configuration.
tags:
  - nanobot
  - dpbot
  - mcp
  - config
  - settings
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

# MCP Configuration

## Overview

MCP server configuration is stored in `/opt/nanobot-data/config.json` under `tools.mcpServers`.

## Configuration Structure

```json
{
  "mcpServers": {
    "homeassistant": {
      "url": "http://192.168.44.19:80/api/mcp",
      "token": "your_bearer_token",
      "headers": {"Host": "localhost"}
    },
    "mariadb": {
      "url": "http://mariadb-mcp:9001/mcp",
      "headers": {"Host": "localhost"}
    }
  }
}
```

## SSRF Whitelist

Private IPs are blocked by default. Hosted MCP targets must be listed in `tools.ssrfWhitelist`:
- `192.168.44.19/32` — Home Assistant
- `172.21.0.0/16` — Docker bridge network (covers unpinned mariadb-mcp container IP)

## Related

- [MCP Config Schema](./mcp-config-schema.md) — Configuration schema and presets
- [MCP Hosted](./mcp-hosted.md) — Hosted MCP servers
- [MCP Local](./mcp-local.md) — Local MCP servers
- [MCP Tools](./mcp-tools.md) — MCP tools
- [Architecture](./architecture.md) — Source ownership