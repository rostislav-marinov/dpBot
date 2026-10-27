---
type: Component
title: dpBot MessageBus (Implementation)
description: >
  MessageBus events and queue in dpBot — inbound message events, outbound
  message delivery, and channel communication.
tags:
  - nanobot
  - agentic-loop
  - bus
  - events
  - queue
  - runtime
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T20:00:00Z
sources:
  - id: dpbot-bus-events
    resource: /projects/dpBot/nanobot/bus/events.py
    title: Bus Events (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
  - id: dpbot-bus-queue
    resource: /projects/dpBot/nanobot/bus/queue.py
    title: Bus Queue (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
---

# MessageBus (Implementation)

The MessageBus handles inbound message events and outbound message delivery
between channels and the agent loop.

## Inbound Messages

Channels translate external platforms into `InboundMessage` events. The bus
queues these events for processing by the AgentLoop.

## Outbound Messages

The AgentLoop publishes `OutboundMessage` events back to the bus, which
routes them to the appropriate channel for delivery to the user.

## Event Flow

```
Channel --> MessageBus[InboundMessage] --> AgentLoop --> AgentRunner --> Tools --> AgentRunner --> AgentLoop --> MessageBus[OutboundMessage] --> Channel
```

## Related

- [Core Flow](./core-flow.md)
- [AgentLoop](./agentloop.md)
- [Channels](./channels.md)
- [dpBot Documentation bundle](../documentation/index.md)
