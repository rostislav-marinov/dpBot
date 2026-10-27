---
okf_version: "0.2"
type: Knowledge Bundle
title: dpBot Agentic Loop Knowledge Bundle
description: >
  Open Knowledge Format (OKF) bundle capturing the agentic loop design of
  the dpBot nanobot fork — the core runtime flow, AgentLoop vs AgentRunner
  split, and the integration points between channels, providers, tools, and
  memory.
type: Knowledge Bundle
tags:
  - nanobot
  - dpbot
  - agentic-loop
  - runtime
  - architecture
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
  - id: docs-concepts
    resource: /projects/dpBot/docs/concepts.md
    title: Concepts (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# dpBot Agentic Loop Knowledge Bundle

This bundle is an Open Knowledge Format (OKF) v0.2 bundle that captures the
agentic loop design of the dpBot nanobot fork.

## Structure

- [Core Flow](./concepts/core-flow.md) — The main runtime loop diagram and ownership split.
- [AgentLoop](./concepts/agentloop.md) — Channel-facing turn orchestration.
- [AgentRunner](./concepts/agentrunner.md) — Model-facing provider/tool loop.
- [Providers](./concepts/providers.md) — LLM backend selection and configuration.
- [Channels](./concepts/channels.md) — User-facing transports and session routing.
- [Tools](./concepts/tools.md) — Built-in and plugin tool discovery and safety.
- [Memory and Sessions](./concepts/memory-sessions.md) — Session replay, long-term memory, and Dream.
- [Context](./concepts/context.md) — Context construction and governance.
- [MessageBus](./concepts/bus.md) — MessageBus events and queue.
- [Hook System](./concepts/hooks.md) — Hook system for turn orchestration.
- [Session Storage](./concepts/session-storage.md) — Session storage implementation.
- [Templates](./concepts/templates.md) — Template system.

## Concepts

Each concept is one markdown file with YAML frontmatter. See the
[spec v0.2](./references/spec-v02.md) for the full format.

## Related

- [dpBot Documentation bundle](../documentation/index.md)
- [OKF Open Knowledge Format skill](../../skills/okf-open-knowledge-format/SKILL.md)
- [dpBot fork skill](../../skills/dpbot-fork/SKILL.md)