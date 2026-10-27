---
type: Component
title: dpBot Channels (Implementation)
description: >
  Channel implementation in dpBot for user-facing transports such as CLI,
  WebUI/WebSocket, Telegram, Discord, Slack, Feishu, WeChat, Email, and others.
type: Component
tags:
  - nanobot
  - agentic-loop
  - channels
  - runtime
  - transport
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:20:00Z
sources:
  - id: dpbot-channels
    resource: /projects/dpBot/nanobot/channels/manager.py
    title: Channel Manager (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
  - id: dpbot-channels-base
    resource: /projects/dpBot/nanobot/channels/base.py
    title: Channel Base (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
---

# Channels (Implementation)

Channel implementation in dpBot for user-facing transports.

## Channel Architecture

Channels translate external platforms into `InboundMessage` events and send
`OutboundMessage` events back to the platform.

## Key Components

### `nanobot/channels/manager.py`
Channel discovery and lifecycle management.

### `nanobot/channels/base.py`
Base channel contract and interface.

### `nanobot/channels/websocket/`
WebSocket/WebUI channel implementation.

## Channel Discovery

Channels are discovered by scanning self-contained packages under
`nanobot/channels/`. Add a channel by contributing one package that follows
[`channel-package-guide.md`](./channel-package-guide.md).

## Supported Channels

- **CLI**: Command-line interface
- **WebUI/WebSocket**: Browser workbench
- **Telegram**: Telegram bot
- **Discord**: Discord bot
- **Slack**: Slack bot
- **Feishu**: Feishu (Lark) integration
- **WeChat**: WeChat integration
- **Email**: Email integration
- **Mattermost**: Mattermost integration
- **Linear**: Linear integration

## Related

- [dpBot Documentation bundle](../documentation/index.md)
- [Channel Package Guide](./channel-package-guide.md)
- [AgentLoop](./agentloop.md)
- [AgentRunner](./agentrunner.md)
- [MessageBus](./bus.md)
- [Session Storage](./session-storage.md)