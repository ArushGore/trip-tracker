# Trip Tracker

Trip Tracker helps frequent travelers accurately track and count their travel days across locations.

## 📁 Repository Layout

- [`/app`](app/) — Go + HTMX + PostgreSQL backend monolith (runs inside an OrbStack Docker container).
- [`/mobile`](mobile/) — Flutter mobile application talking to `/app` endpoints in Phase 1 (and optionally Google Sheets via Google Drive in Phase 2) with full UI parity.
- [`/wiki`](wiki/) — LLMWiki knowledge vault containing all agent documentation, architecture decisions, and SDLC rules.

## 🔄 Development Process (Summary)

1. **Create an Issue** in `arushgore/trip-tracker`.
2. **Write Tests & Acceptance Criteria** before implementation.
3. **3-Lens Review** (Go SDLC best practices, Product Manager UX/Journey, Minimalist Google UI Design) posted as a comment on both the Issue and PR.
4. **Code only after the review lands**, referencing the Issue in any cross-cutting PR.
5. **RED LINE**: Never push directly to `master` without review.

See [`AGENTS.md`](AGENTS.md) and [`wiki/wiki/sdlc-process.md`](wiki/wiki/sdlc-process.md) for complete details.
