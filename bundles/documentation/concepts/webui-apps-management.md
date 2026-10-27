---
type: Concept
title: dpBot WebUI Apps Management
description: >
  WebUI Apps management — Agent Plugins, CLI Apps, and MCP servers in the
  WebUI Apps section.
tags:
  - nanobot
  - dpbot
  - webui
  - apps
  - agent-plugins
  - cli-apps
  - mcp
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:30:00Z
sources:
  - id: docs-webui
    resource: /projects/dpBot/docs/webui.md
    title: WebUI (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# WebUI Apps Management

Open **Apps** from the sidebar to review and manage installable capabilities.
The default **Ready** view shows only capabilities that can be used immediately.

## Agent Plugins

Agent Plugins are local packages that can bundle skills, MCP servers, or both.
A package under `<workspace>/plugins/` is installed but remains inactive until
you enable it in Apps.

## CLI Apps

CLI Apps are local command-line adapters that dpBot runs on your machine.
Their installer manages the executable and exposes its adapter through the
same plugin activation model. Installing an adapter does not modify the native
desktop or web app it connects to.

CLI Apps run with a limited environment that excludes provider API keys. On
Unix, they inherit `XDG_RUNTIME_DIR` when it is set in the gateway's
environment, so desktop CLIs such as Obsidian can locate the running
application. Start the gateway in the same desktop session as the app to
inherit that runtime directory.

## MCP Servers

MCP lists Model Context Protocol servers. Presets provide known
configurations, and the **Add MCP server** panel accepts stdio, HTTP, and SSE
servers. Custom HTTP/SSE servers can use no authentication, OAuth, or request
headers. After saving an OAuth server, choose **Connect** to open its sign-in
page. Presets such as Xmind, Notion, and Linear already use OAuth. HTTPS and
localhost WebUIs return automatically; a remote plain-HTTP WebUI shows one
field for pasting the complete localhost callback URL.

## Using Apps

After a CLI App or MCP server is available, mention it from the composer with
`@` to attach that tool to the next message. Plugin-provided skills
participate in normal skill discovery and can be invoked with `$skill-name`.

## Related

- [WebUI Topics](./webui-topics.md) — Topic management
- [WebUI Workspace](./webui-workspace.md) — Workspace and access
- [WebUI Composer](./webui-composer.md) — Composer, mentions
- [WebUI Skills](./webui-skills.md) — Skills management
- [MCP Configuration](./mcp-config.md) — MCP configuration
- [CLI Plugins](./cli-plugins.md) — Plugin CLI commands
