---
type: Component
title: dpBot Providers (Implementation)
description: >
  Provider selection and configuration in dpBot, including LLM backend
  discovery, model presets, and provider-specific behavior.
type: Component
tags:
  - nanobot
  - agentic-loop
  - providers
  - runtime
  - configuration
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:20:00Z
sources:
  - id: dpbot-providers
    resource: /projects/dpBot/nanobot/providers/factory.py
    title: Provider Factory (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
  - id: dpbot-config-schema
    resource: /projects/dpBot/nanobot/config/schema.py
    title: Config Schema (dpBot source)
    author: nanobot-gateway
    last_modified: 2026-10-22T19:00:00Z
---

# Providers (Implementation)

Provider selection and configuration in dpBot.

## Provider Selection

Provider selection uses this order:

1. **Explicit preset**: If the active preset provider or implicit default provider is not `"auto"`, nanobot uses that provider.
2. **Auto inference**: If provider is `"auto"`, nanobot tries to infer the provider from the model name, configured API keys, local provider base URLs, or gateway providers.
3. **OAuth providers**: Providers such as OpenAI Codex and GitHub Copilot require explicit login and explicit provider/model selection inside the active preset.

## Key Components

### `nanobot/providers/factory.py`
Provider factory for creating LLM providers from configuration.

### `nanobot/config/schema.py`
Configuration schema with provider fields and defaults.

### `nanobot/providers/registry.py`
Provider metadata registry.

## Provider Types

- **OpenAI-compatible**: Most hosted providers use this implementation
- **Anthropic**: Specialized path for Anthropic models
- **Azure OpenAI**: Azure-specific implementation
- **AWS Bedrock**: AWS Bedrock integration
- **Ollama**: Local Ollama integration
- **vLLM**: Local vLLM integration

## Related

- [Configuration](./configuration.md)
- [dpBot Documentation bundle](../documentation/index.md)
- [AgentLoop](./agentloop.md)
- [AgentRunner](./agentrunner.md)