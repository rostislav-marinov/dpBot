---
type: Concept
title: dpBot Provider OAuth Reference
description: >
  Provider OAuth CLI commands for dpBot — authenticating OAuth model
  providers and managing provider credentials.
tags:
  - nanobot
  - dpbot
  - cli
  - providers
  - oauth
  - authentication
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:30:00Z
sources:
  - id: docs-cli-reference
    resource: /projects/dpBot/docs/cli-reference.md
    title: CLI Reference (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# Provider OAuth Reference

| Command | Description |
|---|---|
| `nanobot provider login openai-codex --set-main` | Authenticate Codex and select its current default model |
| `nanobot provider login xai-grok --set-main` | Authenticate an eligible X Premium / Grok subscription and select Grok 4.6; hosted X Search is enabled for models that advertise support |
| `nanobot provider login github-copilot --set-main` | Authenticate GitHub Copilot and select its current default model |
| `nanobot provider logout openai-codex` | Remove OpenAI Codex OAuth state |
| `nanobot provider logout xai-grok --config <path>` | Remove the selected nanobot instance's xAI OAuth state |
| `nanobot provider logout github-copilot` | Remove GitHub Copilot OAuth state |

See [`providers.md`](./providers.md#oauth-providers) for when OAuth providers need explicit provider/model selection.

## Related

- [CLI Agent](./cli-agent.md) — Agent commands
- [Gateway](./cli-gateway.md) — Gateway commands
- [Configuration](./configuration.md) — Provider configuration
- [Architecture](./architecture.md) — Provider selection
- [Security](./security.md) — OAuth security