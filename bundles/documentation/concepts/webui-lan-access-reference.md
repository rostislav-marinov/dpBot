---
type: Concept
title: dpBot WebUI LAN Access Reference
description: >
  WebUI LAN access — opening the WebUI from another device on the same
  network, HTTPS, and remote access controls.
tags:
  - nanobot
  - dpbot
  - webui
  - lan
  - network
  - remote-access
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

# WebUI LAN Access Reference

To open the WebUI from another device on the same network, bind the WebSocket
channel to all interfaces and set a token or token issue secret:

```json
{
  "channels": {
    "websocket": {
      "host": "0.0.0.0",
      "port": 8765,
      "tokenIssueSecret": "your-secret-here"
    }
  }
}
```

The gateway refuses to start with `host` set to `"0.0.0.0"` unless `token` or
`tokenIssueSecret` is configured. After the gateway starts, open
`http://<your-ip>:8765` from the other device and enter the secret in the
login form.

## HTTPS

Plain HTTP is enough for basic WebUI access, but browsers expose microphone
capture only in secure contexts. Voice input works on same-machine localhost;
from another device, serve the WebUI over HTTPS with a certificate that device
trusts. Configure `sslCertfile` and `sslKeyfile` on the WebSocket channel and
open `https://<your-host>:8765`, or terminate HTTPS at a reverse proxy and use
that proxy's HTTPS URL.

## Remote Package Installs

Remote WebUI clients with a valid token can view and use Apps and installed
skills. Actions that install missing nanobot support packages or third-party
marketplace skills are blocked by default. To let trusted remote administrators
perform those installations through the WebUI, opt in explicitly:

```json
{
  "tools": {
    "webuiAllowRemotePackageInstall": true
  }
}
```

Use this only for a private deployment where every authenticated WebUI user is
trusted to change nanobot's Python environment and install workspace skill
instructions or scripts.

## Related

- [WebUI Topics](./webui-topics.md) — Topic management
- [WebUI Workspace](./webui-workspace.md) — Workspace and access
- [WebUI Settings](./webui-settings.md) — Settings
- [Configuration](./configuration.md) — WebSocket channel settings
- [Security](./security.md) — Security boundaries
- [CLI WebUI](./cli-webui.md) — WebUI CLI commands