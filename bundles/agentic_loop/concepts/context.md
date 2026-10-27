---
type: Component
title: dpBot Context Construction (Implementation)
description: >
  Context construction in dpBot — context building, context governance,
  context compaction, and context window management.
tags:
  - nanobot
  - agentic-loop
  - context
  - context-building
  - context-governance
  - runtime
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T20:00:00Z
sources:
  - id: dpbot-context
    resource: /projects/dpBot/nanobot/agent/context.py
    title: Context Builder (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
  - id: dpbot-context-governance
    resource: /projects/dpBot/nanobot/agent/context_governance.py
    title: Context Governance (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
  - id: dpbot-autocompact
    resource: /projects/dpBot/nanobot/agent/autocompact.py
    title: Auto Compact (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
---

# Context Construction (Implementation)

Context construction in dpBot handles how conversation history, workspace
files, memory, and skills are assembled into model-facing context.

## Context Builder

The `ContextBuilder` builds context for an agent turn:

- Combines project instructions with agent-owned profile and memory
- Applies context governance rules
- Prepares the prompt for the model

## Context Governance

Context governance manages context limits and compaction decisions:

- Monitors context window usage
- Decides when to compact
- Applies compaction strategies

## Context Compaction

Auto compact runs when context approaches limits:

- Compacts long conversations automatically when the provider supports it
- Threshold is derived from the active model's context window and reserved
  output headroom
- No provider configuration is required
- Manual compaction via `/compact`

## Context Window Management

- Context window size used by prompt building and consolidation decisions
- Context window size used by prompt building and consolidation decisions
- Context window size used by prompt building and consolidation decisions

## Related

- [Core Flow](./core-flow.md)
- [AgentLoop](./agentloop.md)
- [AgentRunner](./agentrunner.md)
- [Memory and Sessions](./memory-sessions.md)
- [dpBot Documentation bundle](../documentation/index.md)
