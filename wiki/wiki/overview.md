---
title: Overview
tags: [meta, structure, monorepo]
summary: Repository overview and active directories layout description for Trip Tracker.
---

# Workspace Overview

This document provides an overview of the `trip-tracker` repository structure and the `wiki/` knowledge base.

## Top-Level Repository Structure (`arushgore/trip-tracker`)
- `/app/` — Go + HTMX + PostgreSQL backend monolith (deployed inside an OrbStack Docker container).
- `/mobile/` — Flutter mobile application talking to `/app` endpoints (Phase 1) and optionally Google Sheets via Google Drive (Phase 2), with full UI parity.
- `/wiki/` — This LLMWiki knowledge vault containing all agent instructions, architecture docs, and SDLC rules.

## Wiki Directory Structure (`/wiki/`)
- `agents.md` — The global instruction manual governing AI agent processes.
- `index.html` — The client-side dashboard viewer template.
- `llmwiki/` — The rendering engine core (vendored from `ajeygore/llmwiki`).
- `raw/` — Immutable source documents (`2026-11-17-initial-specification.md`).
- `wiki/` — The structured, LLM-maintained knowledge vault:
  - [Architecture & Roadmap](architecture.md)
  - [SDLC & 3-Lens Review Process](sdlc-process.md)
  - [Build Machine & Local Environment](environment-setup.md)
  - [Memory](memory.md), [Context](context.md), [Activity Log](log.md)
