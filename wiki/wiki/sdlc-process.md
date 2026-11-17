---
title: SDLC & 3-Lens Review Process
tags: [sdlc, process, review, git, red-line, go, pm, ui-design]
summary: Mandatory development workflow, 3-Lens review criteria, and git branch rules for Trip Tracker.
---

# SDLC & 3-Lens Review Process

> [!CAUTION]
> **RED LINE — NEVER PUSH TO `master` (OR `main`) WITHOUT REVIEW.**
> At no point may any agent or developer push directly to the default branch without completing the full workflow and receiving review approval on a Pull Request. This is an absolute red line.

---

## 🔄 The 5-Step Development Workflow

Every feature, bugfix, or story **must** follow this exact sequence before any implementation is merged:

1. **Create a GitHub Issue**:
   - Open an Issue in `arushgore/trip-tracker` clearly describing the problem, user story, and scope (noting whether it spans `/app`, `/mobile`, or both).
2. **Write Tests & Acceptance Criteria**:
   - Define explicit Acceptance Criteria and test specifications on the Issue before writing feature code.
3. **Conduct the 3-Lens Review**:
   - Perform a structured review across all three mandatory lenses (see below).
   - Post the 3-Lens Review as a comment on **both the GitHub Issue and the Pull Request** whenever a review is requested.
4. **Gate Coding on Review Landing**:
   - **Only start coding after the review lands.**
   - Work on a dedicated feature branch. Any PR that cuts across `/mobile` and `/app` must explicitly reference the GitHub Issue (`Refs #<issue_number>` / `Closes #<issue_number>`).
5. **Pull Request & Merge**:
   - Open a PR against `master`, attach the 3-Lens Review comment, verify all tests pass inside the OrbStack container environment, and wait for sign-off before merging.

---

## 🔍 The 3-Lens Review Framework

Whenever a review is requested on an Issue or Pull Request, the review comment **must** evaluate the work through these three lenses:

### Lens 1: Go Engineering & SDLC Best Practices
- **Monolith Architecture**: Does this keep the Go service clean, modular, and self-contained without unnecessary microservice sprawl?
- **Concurrency & In-Memory Goroutines**: Are in-memory data structures and background goroutines used effectively and safely (proper synchronization, context cancellation, race-free execution)?
- **Persistence**: Is PostgreSQL persistence used judiciously only where durable state is required, with clean migrations and queries?
- **Testability**: Are unit and integration tests comprehensive and deterministic?

### Lens 2: Product Manager (UX & User Journey)
- **Frequent Traveler Persona**: Does this solve the core day-counting problem accurately and effortlessly for users who travel frequently?
- **Cross-Platform Parity**: Do the web app (`/app` HTMX) and mobile app (`/mobile` Flutter) provide the exact same functional capability and mental model?
- **Edge Cases in Travel**: Are timezone crossings, partial days, overlapping trips, and Phase 2 extensibility (Google Sheets backend) accounted for?

### Lens 3: UI Designer (Minimalist Google Design Guidelines)
- **Material / Google Design Guidelines**: Does the interface follow Google Design Guidelines (clean typography, purposeful whitespace, clear visual hierarchy, Material 3 tokens)?
- **Minimalism**: Is every screen stripped of clutter so a traveler can log or inspect their day count in seconds?
- **Consistency**: Are visual components, spacing, and interactions harmonious between the HTMX web views and the Flutter mobile screens?
