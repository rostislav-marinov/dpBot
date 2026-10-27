---
type: Concept
title: dpBot MCP Configuration Schema
description: >
  MCP configuration schema in dpBot — config fields, presets structure,
  preset usage, and access/capability limits.
tags:
  - nanobot
  - dpbot
  - mcp
  - configuration
  - schema
  - presets
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:30:00Z
sources:
  - id: docs-mcp-presets
    resource: /projects/dpBot/docs/mcp-presets.md
    title: MCP presets (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
  - id: dpbot-config-schema
    resource: /projects/dpBot/nanobot/config/schema.py
    title: Config Schema (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
---

# MCP Configuration Schema

MCP servers are configured under `tools.mcpServers.<name>` in `config.json`:

```json
{
  "tools": {
    "mcpServers": {
      "github": {
        "command": "npx",
        "args": ["-y", "@modelcontextprotocol/server-github"],
        "env": { "GITHUB_PERSONAL_ACCESS_TOKEN": "${GITHUB_TOKEN}" }
      },
      "remote": {
        "url": "https://example.com/mcp/",
        "headers": { "Authorization": "Bearer ${REMOTE_MCP_TOKEN}" }
      }
    }
  }
}
```

## Configuration Fields

| Field | Type | Required | Description |
|---|---|---|---|
| `command` | string | Yes (for stdio) | Command to run the MCP server |
| `args` | array | Yes (for stdio) | Arguments to pass to the command |
| `env` | object | No | Environment variables for the server |
| `url` | string | Yes (for HTTP/SSE) | URL of the MCP server |
| `headers` | object | No | HTTP headers for the server |

## MCP Presets

MCP presets provide known configurations for common services. They are
maintained in `nanobot/webui/mcp_presets.json` and validated by the gateway
when loading.

### Preset Structure

Each preset declares:

- Server configuration (command, args, env, url, headers)
- Setup fields (type, label, help text)
- Validation rules

### Using Presets

1. Open **Apps → MCP** in the WebUI
2. Search for a service
3. Configure its connection
4. Select **Connect**

Presets save MCP server configuration; the gateway discovers and runs the
tools.

## Access and Capability Limits

- A listing in another product's plugin directory does not supply a portable
  MCP URL or reusable credentials
- Native OAuth presets require authorization-server discovery and dynamic
  client registration
- Services that require a fixed OAuth client, client allowlisting, or
  additional onboarding need their own setup

## Provider Plans, Quotas, Enabled Tools

- Provider plans, quotas, enabled tools, and organization policies still apply
- A configured connection is distinct from a connected runtime
- Tool access follows provider permissions and nanobot's configured policy

## Related

- [MCP Configuration](./mcp-config.md) — MCP server configuration
- [MCP Presets](./mcp-presets.md) — Hosted MCP service presets
- [MCP Local Presets](./mcp-local-presets.md) — Local MCP server presets
- [MCP Tools](./mcp-tools.md) — Tool discovery and safety
- [Configuration](./configuration.md) — Config file and schema
