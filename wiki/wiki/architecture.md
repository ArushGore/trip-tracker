---
title: Architecture & Roadmap
tags: [architecture, backend, mobile, go, htmx, postgres, flutter, orbstack]
summary: System architecture, phase roadmap, and environment topology for the Trip Tracker application.
---

# Architecture & Roadmap

**Trip Tracker** is an application designed for frequent travelers who need to accurately track and count their travel days across jurisdictions.

---

## 🏗️ Monorepo Structure

The repository (`arushgore/trip-tracker`) is organized into three top-level directories:
- `/app/` — Go + HTMX + PostgreSQL backend and web UI application.
- `/mobile/` — Flutter mobile application (iOS/Android) sharing UI parity and endpoints with `/app/`.
- `/wiki/` — LLMWiki knowledge vault containing all agent instructions, architecture docs, SDLC workflows, and project memory.

---

## 🗺️ Phased Roadmap

### Phase 1: Core Backend & Mobile Parity (Current)
- **Backend (`/app`)**: Built as a Go monolith serving HTMX-powered web views and JSON/REST API endpoints, backed by PostgreSQL.
- **Mobile (`/mobile`)**: Built with Flutter, communicating directly with the `/app` endpoints and providing the exact same UI functionality and user flows as the web app.
- **Storage**: All persistence goes through the Trip Tracker backend (`/app`) into the PostgreSQL container.

### Phase 2: Dual-Backend & Google Sheets Integration (Future)
- **Pluggable Backend**: Users on the Flutter mobile app can choose between:
  1. **Trip Tracker Backend** (`/app` API)
  2. **Google Sheets Backend** (standalone mode without our backend server)
- **Google Drive & Sheets API**: When Google Sheets is selected as the backend, the mobile app connects directly to the user's Google Drive / Google Sheets to read and persist trip records.

---

## ⚙️ Backend Engineering Principles (`/app`)

1. **Go Monolith**: Single self-contained binary serving both HTMX hypermedia responses and mobile API endpoints.
2. **In-Memory Goroutines**: Leverage Go concurrency primitives (in-memory state, worker goroutines, channels, and fast caching) where appropriate, persisting to PostgreSQL when durable storage is required.
3. **Database**: PostgreSQL running strictly inside an OrbStack Docker container (**never** installed directly on the host macOS machine).

---

## 🌐 Networking & Deployment Topology

| Environment | Protocol & Port | Execution Runtime | Access Method |
| :--- | :--- | :--- | :--- |
| **Local Development** | HTTP (non-SSL, e.g. `:8080`) | Docker container inside **OrbStack** | Open locally in browser via port forwarding; mobile simulator/device connects over non-SSL port |
| **Production** | HTTPS (`:443` SSL) | Containerized deployment | Mobile app and web clients connect strictly over port `443` |
