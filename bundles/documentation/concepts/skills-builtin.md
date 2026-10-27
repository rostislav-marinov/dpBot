---
type: Concept
title: dpBot Built-in Skills
description: >
  Built-in skills bundled with dpBot — core nanobot skills.
tags:
  - nanobot
  - dpbot
  - skills
  - built-in
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:30:00Z
sources:
  - id: docs-concepts
    resource: /projects/dpBot/docs/concepts.md
    title: Concepts (docs)
    author: process:dpbot-docs
    last_modified: 2026-10-22T19:00:00Z
---

# Built-in Skills

Built-in skills are bundled with dpBot and always available.

## Discovery and Invocation

Skills are discovered from:

1. Built-in skills under `nanobot/skills/`
2. Workspace skills under `<workspace>/skills/`
3. Plugin-provided skills from Agent Plugins

## Available Built-in Skills

| Skill | Description | Tags |
|---|---|---|
| `cron` | Schedule reminders and recurring tasks | scheduling |
| `weather` | Get current weather and forecasts | weather |
| `memory` | Search past conversations in the agent's history log | memory |
| `skill-creator` | Create, update, or package agent skills | packaging |
| `update-setup` | Set up or reconfigure nanobot's upgrade skill | upgrade |
| `my` | Inspect or troubleshoot the agent's runtime state | runtime |
| `tdd` | Test-driven development | testing |
| `codebase-design` | Shared vocabulary for designing deep modules | design |
| `writing-for-agents` | Writing documents for agents | documentation |
| `lucid-dream` | Maintain the LUCID_DREAM.md efficiency rule catalogue | efficiency |
| `okf-open-knowledge-format` | Create, validate, and enrich Open Knowledge Format bundles | OKF |
| `gerena-events` | Check for upcoming football matches or publicly announced events at Gerena stadium | events |
| `home-assistant-inspection` | Inspect and repair the Home Assistant instance | HA |
| `home-lab-monitoring` | Run, verify and troubleshoot the home-lab monitoring reports | monitoring |
| `home-lab-ssh` | Connect to and inspect the home-lab hosts from the nanobot container over SSH | SSH |
| `dpbot-fork` | Work on dpBot, Rosko's fork of nanobot | dpbot |
| `grilling` | Grill the user relentlessly about a plan, decision, or idea | interview |
| `to-questionnaire` | Turn a decision you can't fully answer into a questionnaire for someone else to fill in | questionnaire |
| `teach` | Teach the user a new skill or concept within this workspace | teaching |
| `handoff` | Compact the current conversation into a handoff document for another agent to pick up | handoff |
| `multi-stage-dockerfile` | Create optimized multi-stage Dockerfiles for any language or framework | Docker |
| `wait-what` | Stop. That last message did not land: re-pitch it | clarification |
| `grill-me` | A relentless interview to sharpen a plan or design | interview |
| `clawhub` | Search and install agent skills from ClawHub, the public skill registry | registry |
| `nanobot-document` | Answer nanobot usage, configuration, and troubleshooting questions from its bundled documentation | documentation |
| `image-generation` | Generate images and iteratively edit saved image artifacts | image-processing |

## Related

- [Built-in Skills Catalog](./skills-builtin-catalog.md) — Bundled skills catalog
- [Workspace Skills](./skills-workspace.md) — User-provided skills
- [Skills Marketplace](./skills-marketplace.md) — Marketplace skills
- [WebUI Skills](./webui-skills.md) — Skills management in browser
- [Architecture](./architecture.md) — Source ownership