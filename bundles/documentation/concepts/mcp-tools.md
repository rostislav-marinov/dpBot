---
type: Concept
title: dpBot MCP Tools
description: >
  MCP tools in dpBot — MCP tool access.
tags:
  - nanobot
  - dpbot
  - mcp
  - tools
  - api
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

# MCP Tools

## Overview

MCP tools provide API access to configured MCP servers.

## Available Tools

| Tool | Description |
|---|---|
| `homeassistant` | Access Home Assistant MCP API |
| `mariadb` | Access MariaDB MCP API |

## Usage

MCP tools are accessed through the nanobot Python gateway.

## Related

- [MCP Hosted](./mcp-hosted.md) — Hosted MCP servers
- [MCP Local](./mcp-local.md) — Local MCP servers
- [MCP Config](./mcp-config.md) — MCP configuration
- [Architecture](./architecture.md) — Source ownership