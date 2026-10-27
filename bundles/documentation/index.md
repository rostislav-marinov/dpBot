---
okf_version: "0.2"
type: Knowledge Bundle
title: dpBot Documentation Knowledge Bundle
description: >
  Open Knowledge Format (OKF) bundle capturing the documentation of the
  dpBot nanobot fork — its architecture, configuration, memory, operations,
  and development conventions.
type: Knowledge Bundle
tags:
  - nanobot
  - dpbot
  - documentation
  - okf
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:10:00Z
---

# dpBot Documentation Knowledge Bundle

This bundle is an Open Knowledge Format (OKF) v0.2 bundle that captures the
documentation of the dpBot nanobot fork at `/projects/dpBot`.

## Structure

- [Architecture](./concepts/architecture.md) — Source ownership and architecture overview.
- [Architecture Runtime Flow](./concepts/architecture-runtime.md) — Runtime flow, source ownership, extension points.
- [Configuration](./concepts/configuration.md) — Config schema, model presets, tools, security.
- [Memory](./concepts/memory.md) — Long-term memory, Dream consolidation, lucid-dream.
- [Operations](./concepts/operations.md) — Deployment, monitoring, cron jobs, home-lab context.
- [CLI Agent](./concepts/cli-agent.md) — Agent CLI overview.
- [CLI Agent Reference](./concepts/cli-agent-reference.md) — Detailed CLI Agent commands.
- [CLI Gateway](./concepts/cli-gateway.md) — Gateway CLI overview.
- [CLI Gateway Reference](./concepts/cli-gateway-reference.md) — Detailed gateway commands.
- [CLI Serve](./concepts/cli-serve.md) — Serve CLI overview.
- [CLI Serve Reference](./concepts/cli-serve-reference.md) — Detailed serve commands.
- [CLI WebUI](./concepts/cli-webui.md) — WebUI CLI overview.
- [CLI WebUI Reference](./concepts/cli-webui-reference.md) — Detailed WebUI commands.
- [CLI Status](./concepts/cli-status.md) — Status CLI overview.
- [CLI Status Reference](./concepts/cli-status-reference.md) — Detailed status commands.
- [CLI Channels](./concepts/cli-channels.md) — Channels CLI overview.
- [CLI Channels Reference](./concepts/cli-channels-reference.md) — Detailed channel commands.
- [CLI Plugins](./concepts/cli-plugins.md) — Plugins CLI overview.
- [CLI Plugins Reference](./concepts/cli-plugins-reference.md) — Detailed plugin commands.
- [CLI Providers](./concepts/cli-providers.md) — Providers CLI overview.
- [CLI Providers Reference](./concepts/cli-providers-reference.md) — Detailed provider commands.
- [WebUI Topics](./concepts/webui-topics.md) — Topics, conversation groups, panes.
- [WebUI Activity](./concepts/webui-activity.md) — Activity, context usage, model failures.
- [WebUI Temporary](./concepts/webui-temporary.md) — Temporary chats.
- [WebUI Workspace](./concepts/webui-workspace.md) — Workspace picker, project selection, access control.
- [WebUI Workspace and Access Reference](./concepts/webui-workspace-access-reference.md) — Detailed workspace reference.
- [WebUI Composer](./concepts/webui-composer.md) — Composer, mentions, input.
- [WebUI Composer Reference](./concepts/webui-composer-reference.md) — Detailed composer reference.
- [WebUI Channels](./concepts/webui-channels.md) — Channels overview.
- [WebUI Channels Reference](./concepts/webui-channels-reference.md) — Detailed channel management reference.
- [WebUI Apps](./concepts/webui-apps.md) — Apps section changes.
- [WebUI Apps Management](./concepts/webui-apps-management.md) — Apps management overview.
- [WebUI Skills](./concepts/webui-skills.md) — Skills management overview.
- [WebUI Skills Management Reference](./concepts/webui-skills-management-reference.md) — Detailed skills management reference.
- [WebUI Automations](./concepts/webui-automations.md) — Automations view.
- [WebUI Settings](./concepts/webui-settings.md) — Settings overview.
- [WebUI Settings Reference](./concepts/webui-settings-reference.md) — Detailed settings reference.
- [WebUI LAN Access](./concepts/webui-lan.md) — LAN access overview.
- [WebUI LAN Access Reference](./concepts/webui-lan-access-reference.md) — Detailed LAN access reference.
- [WebUI Delegated](./concepts/webui-delegated.md) — Delegated work overview.
- [WebUI Delegated Work Reference](./concepts/webui-delegated-work-reference.md) — Detailed delegated work reference.
- [MCP Hosted](./concepts/mcp-hosted.md) — Configured hosted MCP servers.
- [MCP Local](./concepts/mcp-local.md) — Configured local MCP servers.
- [MCP Configuration](./concepts/mcp-config.md) — MCP configuration and presets.
- [MCP Config Schema](./concepts/mcp-config-schema.md) — MCP configuration schema.
- [MCP Tools](./concepts/mcp-tools.md) — MCP tool access.
- [MCP Tool Discovery and Safety](./concepts/mcp-tool-discovery-safety.md) — Tool discovery and safety.
- [MCP Presets](./concepts/mcp-presets.md) — Hosted MCP service presets.
- [MCP Local Presets](./concepts/mcp-local-presets.md) — Local MCP server presets.
- [Automations Scheduled](./concepts/automations-scheduled.md) — Cron, interval, one-time tasks.
- [Automations Triggers](./concepts/automations-triggers.md) — Local triggers.
- [Automations Heartbeat](./concepts/automations-heartbeat.md) — Heartbeat.
- [Skills](./concepts/skills.md) — Skills system.
- [Subagents](./concepts/subagents.md) — Subagent delegation.
- [Security](./concepts/security.md) — Security boundaries.
- [Update Protocol](./concepts/update.md) — Update and release procedures.

## Concepts

Each concept is one markdown file with YAML frontmatter. See the
[spec v0.2](./references/spec-v02.md) for the full format.

## Related

- [OKF Open Knowledge Format skill](../../skills/okf-open-knowledge-format/SKILL.md)
- [dpBot fork skill](../../skills/dpbot-fork/SKILL.md)