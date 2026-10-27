---
type: Concept
title: dpBot OpenAI-Compatible API CLI Reference
description: >
  OpenAI-compatible API CLI commands for dpBot — serving
  `/v1/chat/completions`, `/v1/models`, and `/health` endpoints.
tags:
  - nanobot
  - dpbot
  - cli
  - serve
  - api
  - openai
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

# OpenAI-Compatible API CLI Reference

`nanobot serve` starts an OpenAI-compatible API server for programmatic access.

## Starting the API Server

| Command | Description |
|---|---|
| `nanobot serve` | Start `/v1/chat/completions`, `/v1/models`, `/health` |
| `nanobot serve --host <host>` | Override API bind host |
| `nanobot serve --port <port>` | Override API port |
| `nanobot serve --timeout <seconds>` | Override per-request timeout |
| `nanobot serve --workspace <path>` | Override workspace |
| `nanobot serve --config <path>` | Use specific config file |

## API Endpoints

Default API endpoint: `http://127.0.0.1:8900`

Public binds (`0.0.0.0` or `::`) require `api.apiKey`; send it as a Bearer token on API routes.

## Related

- [CLI Serve](./cli-serve.md) — CLI Serve overview
- [Agent CLI](./cli-agent.md) — Agent commands
- [Gateway](./cli-gateway.md) — Gateway commands
- [Configuration](./configuration.md) — Config file and schema
- [Architecture](./architecture.md) — API runtime
- [Security](./security.md) — Security boundaries