---
title: Memory
tags: [meta, memory, learnings, rules]
summary: A compiled record of long-term agent memories, architectural decisions, and red-line rules.
---

# Agent Memory

This file acts as a persistent memory bank where visiting AI agents document long-term learnings, persistent takeaways, and critical rules compiled across sessions.

## 🚨 Red-Line Rules (Never Violate)
1. **Never push directly to `master`**: Every change must go through a branch, PR, and review.
2. **Never code before the 3-Lens Review lands**: Follow the strict sequence:
   - Step 1: Create GitHub Issue in `arushgore/trip-tracker`.
   - Step 2: Write tests and acceptance criteria.
   - Step 3: Post the **3-Lens Review** (Go SDLC best practices, Product Manager UX/Journey, Minimalist Google UI Design) as a comment on the Issue (and later on the PR).
   - Step 4: Only begin coding after the review lands. Cross-cutting changes across `mobile` and `app` must reference the Issue in the PR.
3. **Never install PostgreSQL locally on macOS**: PostgreSQL and the `/app` deployment must run inside Docker containers on **OrbStack**.

## 🏗️ Architectural Takeaways
- **Product Goal**: Help frequent travelers accurately count and track their days across trips/locations.
- **Phase 1**: Flutter mobile app (`/mobile`) and HTMX web UI talk to the Go monolith backend (`/app`) backed by PostgreSQL in OrbStack. Mobile and web share identical UI functionality.
- **Phase 2**: Optional standalone mode where `/mobile` connects directly to the user's Google Sheets (via Google Drive access) as an alternative backend.
- **Networking**:
  - Production: Mobile app talks to `/app` over port `443` (HTTPS).
  - Local Dev: `/app` runs in an OrbStack Docker container with port forwarding to the host browser and mobile client over a non-SSL port.
- **Go Design**: Monolith architecture utilizing in-memory goroutines for fast state/concurrency and PostgreSQL when durable persistence is required.
