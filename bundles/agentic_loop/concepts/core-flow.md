---
type: Concept
title: dpBot Core Flow
description: >
  The main runtime flow of the dpBot nanobot agentic loop, from inbound
  channel message to outbound reply.
tags:
  - nanobot
  - agentic-loop
  - runtime
  - core-flow
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:20:00Z
sources:
  - id: docs-architecture
    resource: /projects/dpBot/docs/architecture.md
    title: Architecture (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# Core Flow

The main runtime flow of the dpBot agentic loop:

```mermaid
flowchart LR
    Channel["Channel<br/>CLI, WebUI, chat apps"] --> Bus["MessageBus<br/>InboundMessage"]
    Bus --> Loop["AgentLoop<br/>session, workspace, context"]
    Loop --> Runner["AgentRunner<br/>provider/tool loop"]
    Runner --> Provider["Provider<br/>LLM backend"]
    Provider --> Runner
    Runner --> Tools["Tools<br/>files, shell, web, MCP, cron"]
    Tools --> Runner
    Runner --> Loop
    Loop --> Outbound["MessageBus<br/>OutboundMessage"]
    Outbound --> Channel

    Loop -. reads/writes .-> State["Session, memory,<br/>hooks, skills, templates"]
```

## Ownership

- `AgentLoop` owns the channel-facing turn.
- `AgentRunner` owns the model-facing loop.

## Related

- [AgentLoop](./agentloop.md)
- [AgentRunner](./agentrunner.md)
- [Context](./context.md)
- [MessageBus](./bus.md)
- [Hook System](./hooks.md)
- [Session Storage](./session-storage.md)
- [Templates](./templates.md)
- [dpBot Documentation bundle](../documentation/index.md)