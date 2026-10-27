---
type: Reference
title: OKF Spec v0.2
description: >
  The Open Knowledge Format v0.2 specification, bundled as a reference
  for this OKF bundle.
tags:
  - okf
  - spec
  - reference
status: draft
generated:
  by: reference_agent/gemini-2.5-pro
  at: 2026-10-22T19:20:00Z
sources:
  - id: okf-spec
    resource: https://github.com/GoogleCloudPlatform/open-knowledge-format
    title: Open Knowledge Format
    author: Google Cloud
    last_modified: 2026-10-22T19:00:00Z
---

# OKF Spec v0.2

OKF is an open, human- and agent-friendly format for representing knowledge:
the metadata, context, and curated insight that surrounds data and systems.

The format is intentionally minimal: a directory of markdown files with
YAML frontmatter. There is no schema registry, no central authority, and no
required tooling. If you can `cat` a file, you can read OKF; if you can
`git clone` a repo, you can ship it.

## Bundle Structure

A bundle is a directory tree of markdown files. The directory structure
is independent of the domain: producers organize concepts however makes
sense for the knowledge being captured.

```
path/to/bundle/
  index.md                      # Optional. Directory listing for progressive disclosure.
  log.md                        # Optional. Chronological history of updates.
  <concept>.md                  # A concept at the bundle root.
  <subdirectory>/               # Subdirectories organize concepts into groups.
    index.md
    <concept>.md
    <subdirectory>/
      ...
```

## Reserved Filenames

| Filename   | Purpose                          |
|------------|----------------------------------|
| `index.md` | Directory listing.               |
| `log.md`   | Update history.                  |

All other `.md` files are concept documents.

## Core Fields

| Field | Required? | Description |
|-------|-----------|-------------|
| `type` | **YES** | Kind of concept (free-form string) |
| `title` | Recommended | Human-readable display name |
| `description` | Recommended | One-sentence summary |
| `tags` | Optional | YAML list for cross-cutting categorization |

## Trust & Lifecycle Fields

| Field | Description |
|-------|-------------|
| `generated` | `{ by: <actor>, at: <ISO8601> }` — Who/what created this content and when |
| `verified` | List of `{ by: <actor>, at: <ISO8601> }` — Who confirmed correctness |
| `status` | `draft` \| `stable` \| `deprecated` — Default: `stable` |
| `stale_after` | ISO 8601 datetime — Content is stale on/after this instant |

## Provenance Fields

| Field | Description |
|-------|-------------|
| `sources` | List of source entries |
| `usage_window` | `{ from, to }` — Time range for `usage_count` signals |

Each `sources` entry:
- `resource` (REQUIRED): URL, bundle-relative path, or scope descriptor
- `id`: Stable key for footnote attribution
- `title`: Human-readable label
- `author`: Actor who produced the source
- `usage_count`: How often exercised (liveness signal)
- `last_modified`: When the source last changed

## Actor Convention

Fields that record identity use:
- `<producer>/<version>` for agents: `reference_agent/gemini-2.5-pro`
- `human:<id>` for people: `human:ahormati`
- `process:<id>` for automation: `process:finance-nightly`

Trust tiers are derived from the `human:` prefix —
human-verified > machine-confirmed > unverified.

## Conformance

Three rules — all must pass:
1. Every non-reserved `.md` file has parseable YAML frontmatter.
2. Every frontmatter has a non-empty `type` field.
3. Reserved files (`index.md`, `log.md`) follow their defined structure when present.