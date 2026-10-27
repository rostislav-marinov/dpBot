---
type: Concept
title: dpBot MCP Tool Discovery and Safety
description: >
  MCP tool discovery and safety in dpBot — tool discovery, SSRF protection,
  and security controls for MCP servers.
tags:
  - nanobot
  - dpbot
  - mcp
  - tools
  - safety
  - ssrf
  - security
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
  - id: docs-configuration
    resource: /projects/dpBot/docs/configuration.md
    title: Configuration (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# MCP Tool Discovery and Safety

## Tool Discovery

After an MCP server is available, mention it from the composer with `@` to
attach that tool to the next message. Plugin-provided skills participate in
normal skill discovery and can be invoked with `$skill-name`.

## SSRF Protection

nanobot uses a shared SSRF guard for built-in web fetches and HTTP/SSE MCP
connections. By default it blocks:

- Loopback addresses
- RFC1918/private ranges
- CGNAT/Tailscale ranges
- Link-local addresses
- Cloud metadata endpoints

If you need to allow trusted private ranges, explicitly exempt them from
SSRF blocking with `tools.ssrfWhitelist`:

```json
{
  "tools": {
    "ssrfWhitelist": ["100.64.0.0/10"]
  }
}
```

Keep whitelist entries as narrow as possible, such as a single host CIDR
(`192.168.1.50/32`). The whitelist is global for the shared SSRF guard; it is
not limited to one tool or one MCP server.

## Proxy Behavior

HTTP/SSE MCP connections use the same process-wide proxy environment behavior
as `web_fetch`: proxied targets use the configured proxy, and URLs excluded by
`NO_PROXY` remain DNS-pinned direct connections.

## Related

- [MCP Configuration](./mcp-config.md) — MCP configuration and presets
- [MCP Hosted](./mcp-hosted.md) — Hosted MCP servers
- [MCP Local](./mcp-local.md) — Local MCP servers
- [WebUI Apps](./webui-apps.md) — Apps management
- [Security](./security.md) — Security boundaries
- [Configuration](./configuration.md) — SSRF whitelist settings