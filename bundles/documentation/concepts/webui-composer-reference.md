---
type: Concept
title: dpBot WebUI Composer Reference
description: >
  WebUI composer — input handling, attachments, voice, slash commands, and
  topic mentions.
tags:
  - nanobot
  - dpbot
  - webui
  - composer
  - input
  - attachments
  - voice
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

# WebUI Composer Reference

The composer supports plain messages, image attachments, voice input (when
transcription is configured), slash commands, and `@` mentions for installed
Apps, MCP presets, or saved topics.

## Topic Mentions

- To reference another topic, type or paste its complete handle (such as
  `@luma`), choose it from the `@` menu, or drag it from the sidebar
- Recognized handles are highlighted; unknown handles remain plain text
- You can reference up to eight different topics in one message
- Ask nanobot to find, read, or send messages to other saved topics, including
  those in other projects
- Mentioning a topic alone does not send a message to it

## Input Handling

- On desktop, **Enter** sends and **Shift+Enter** adds a newline
- On touch devices, **Enter** inserts a newline; tap the send arrow to submit
- While a response is running, desktop Enter adds your input to one waiting
  message; further inputs append in order, separated by newlines, with their
  attachments and references retained
- Press Enter again with an empty input or choose **Send now** to insert it
  immediately as guidance for the active turn

## Attachments and Voice

- Image attachments use a compact gallery, showing at most four thumbnails
  before a count of the remaining images
- With voice transcription configured, the idle composer uses one button for
  voice input when empty and Send when text or attachments are present
- Speech is transcribed into the draft before sending

## Slash Commands

- Type `/` to discover nanobot commands and terminal navigation in one palette
- Type `@` to complete installed apps, configured MCP servers, and saved
  sessions
- Use the arrow keys to choose an item and Tab to complete it

## Related

- [WebUI Topics](./webui-topics.md) — Topic management
- [WebUI Workspace](./webui-workspace.md) — Workspace and access
- [WebUI Activity](./webui-activity.md) — Activity and context usage
- [WebUI Channels](./webui-channels.md) — Channel management
- [WebUI Apps](./webui-apps.md) — Apps management
- [WebUI Skills](./webui-skills.md) — Skills management
- [WebUI Automations](./webui-automations.md) — Automations view
- [WebUI Settings](./webui-settings.md) — Settings
- [WebUI LAN Access](./webui-lan.md) — LAN access
- [Configuration](./configuration.md) — Config file and schema
- [Security](./security.md) — Security boundaries