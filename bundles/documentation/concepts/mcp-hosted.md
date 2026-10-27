---
type: Concept
title: dpBot MCP Hosted
description: >
  Hosted MCP servers in dpBot — configured remote MCP endpoints.
tags:
  - nanobot
  - dpbot
  - mcp
  - hosted
  - remote
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

# MCP Hosted

## Overview

Hosted MCP servers are remote MCP endpoints accessible over HTTP.

## Available Hosted MCP Servers

| Server | URL | Description |
|---|---|---|
| `homeassistant` | `http://192.168.44.19:80/api/mcp` | Home Assistant MCP server |
| `mariadb` | `http://mariadb-mcp:9001/mcp` | MariaDB MCP server |

## Configuration

Hosted MCP servers are configured in `/opt/nanobot-data/config.json` under `tools.mcpServers`.

## Related

- [MCP Presets](./mcp-presets.md) — Hosted MCP service presets
- [MCP Local](./mcp-local.md) — Local MCP servers
- [MCP Config](./mcp-config.md) — MCP configuration
- [MCP Tools](./mcp-tools.md) — MCP tools
- [Architecture](./architecture.md) — Source ownership