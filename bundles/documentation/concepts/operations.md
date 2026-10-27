---
type: Concept
title: dpBot Operations
description: >
  Deployment, monitoring, cron jobs, and home-lab context for the
  dpBot nanobot fork running on dpSrvA.
tags:
  - nanobot
  - operations
  - deployment
  - monitoring
  - cron
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:10:00Z
sources:
  - id: docs-deployment
    resource: /projects/dpBot/docs/deployment.md
    title: Deployment (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
  - id: docs-automations
    resource: /projects/dpBot/docs/automations.md
    title: Automations (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
  - id: SOUL
    resource: /home/nanobot/.nanobot/workspace/SOUL.md
    title: SOUL.md
    author: nanobot
    last_modified: 2026-10-22T19:00:00Z
---

# Operations

## Runtime Environment

The dpBot fork runs as `nanobot-gateway` in Docker on dpSrvA
(192.168.44.20, NanoPi Zero2, aarch64, 1968 MiB RAM, SD-card storage).

Container limits: memory.max 1 GiB, memory.swap.max 2 GiB, 1 CPU.

## Gateway Management

```bash
# Start gateway
nanobot gateway

# Start in background
nanobot gateway --background

# Status
nanobot gateway status

# Logs
nanobot gateway logs

# Stop
nanobot gateway stop
```

## Cron Jobs

Cron job definitions live in `/home/nanobot/.nanobot/workspace/cron/jobs.json`.

### Adopted Monitoring Jobs

| Job ID | Schedule | Script | Purpose |
|---|---|---|---|
| `78708e16` | `0 9,15,21 * * *` | `scripts/host_monitor.sh` | 9-host online check, temperatures |
| `4671e8bd` | `0 9,21 * * *` | `scripts/dup_mac_report.sh` | Router ARP + DHCP duplicate MAC |
| `4e5bfd93` | `0 9,21 * * *` | `scripts/traffic_report.sh` | LAN traffic top-5 (14-day) |
| `b5f3ec48` | `0 16 * * *` | `gerena-events-daily` | Football match schedule |

### Lucid Dream Job

| Job ID | Schedule | Purpose |
|---|---|---|
| `ef4f11a7` | `0 2 * * *` Europe/Sofia | Efficiency rule audit and consolidation |

## MCP Servers

Both MCP servers are configured in `/opt/nanobot-data/config.json`:

- `homeassistant` → `http://192.168.44.19:80/api/mcp` with bearer token.
- `mariadb` → `http://mariadb-mcp:9001/mcp` with `Host: localhost` header.

## Home Lab Context

- dpSrvA: 192.168.44.20 (NanoPi Zero2)
- dpAuto: 192.168.44.19 (Home Assistant)
- dpNAS: 192.168.44.x
- dpRtr: Router at 192.168.44.1

Network layout maintained in `network_layout.md`.

## Related

- [Configuration](./configuration.md) — Config file location and format.
- [Memory](./memory.md) — Workspace and session paths.
- [Automations](./automations.md) — Cron, triggers, heartbeat.