---
type: Concept
title: dpBot Security Boundaries
description: >
  Security-sensitive code paths and boundaries in dpBot — workspace scope,
  shell sandboxing, SSRF/network checks, PTH guard, channel access control,
  and security configuration.
tags:
  - nanobot
  - dpbot
  - security
  - boundaries
  - sandbox
  - ssrf
  - workspace
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:30:00Z
sources:
  - id: docs-architecture
    resource: /projects/dpBot/docs/architecture.md
    title: Architecture (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
  - id: docs-configuration
    resource: /projects/dpBot/docs/configuration.md
    title: Configuration (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# Security Boundaries

Security-sensitive code paths in dpBot include:

## Workspace Scope

| Boundary | Files |
|---|---|
| Workspace scope | `nanobot/security/workspace_access.py`, `nanobot/security/workspace_policy.py` |
| Shell sandboxing | `nanobot/agent/tools/shell.py` |
| SSRF/network checks | `nanobot/security/network.py`, `nanobot/agent/tools/web.py` |
| PTH guard and CLI startup security | `nanobot/security/` and CLI entrypoints |
| Channel access control | Channel config in `nanobot/channels/*.py` |

## Configuration

| Setting | Description |
|---|---|
| `tools.restrictToWorkspace` | Restrict file/shell tools to the workspace |
| `tools.exec.sandbox` | Sandbox shell execution |
| `tools.ssrfWhitelist` | Allowlist for outbound HTTP requests |
| `channels.*.allowFrom` | Restrict which chat-app senders may interact |

## Channel Access Control

Configure per-channel access policies to restrict who can interact with
dpBot through each chat platform.

## PTH Guard and CLI Startup Security

The PTH (Protected Terminal Hardware) guard and CLI startup security
prevent unauthorized access to the agent runtime.

## Related

- [Architecture](./architecture.md) — Source ownership and runtime flow
- [Configuration](./configuration.md) — Config file and schema
- [WebUI](./webui.md) — Channel settings and access controls
- [CLI Reference](./cli.md) — Security-sensitive commands
