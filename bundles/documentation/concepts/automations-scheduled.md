---
type: Concept
title: dpBot Automations Scheduled
description: >
  Scheduled automations in dpBot — cron-based tasks that run at specified intervals.
tags:
  - nanobot
  - dpbot
  - automations
  - scheduled
  - cron
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:30:00Z
sources:
  - id: docs-automations
    resource: /projects/dpBot/docs/automations.md
    title: Automations (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# Automations Scheduled

## Overview

Scheduled automations in dpBot are cron-based tasks that run at specified intervals.

## Available Automations

| Automation | ID | Schedule | Description |
|---|---|---|---|
| `host-monitor-report` | `78708e16` | 0 9,15,21 * * * | Host status and temperatures |
| `dup-mac-scan` | `4671e8bd` | 0 9,21 * * * | Duplicate MAC scan |
| `traffic-top5-14day-report` | `4e5bfd93` | 0 9,21 * * * | 14-day LAN traffic top-5 |
| `gerena-events-daily` | `b5f3ec48` | 0 16 * * * | Gerena events daily |

## Related

- [Automations Triggers](./automations-triggers.md) — Event triggers
- [Automations Heartbeat](./automations-heartbeat.md) — Heartbeat tasks
- [Architecture](./architecture.md) — Source ownership