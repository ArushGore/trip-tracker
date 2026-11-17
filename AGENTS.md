# Trip Tracker — Agent Instructions

All project rules, architecture documentation, long-term memory, active context, and custom skills are maintained centrally in our LLMWiki inside the [`/wiki/`](wiki/) directory.

## 📖 Mandatory Reading Before Any Task
1. [`wiki/agents.md`](wiki/agents.md) — Core LLMWiki operating manual (Ingest, Query, Lint, and Reprocess flows).
2. [`wiki/wiki/memory.md`](wiki/wiki/memory.md) — Red-line rules and core architectural decisions.
3. [`wiki/wiki/sdlc-process.md`](wiki/wiki/sdlc-process.md) — The 5-step Issue-first development workflow and 3-Lens Review framework.
4. [`wiki/wiki/architecture.md`](wiki/wiki/architecture.md) — Phase 1 & Phase 2 system design (Go + HTMX + Postgres in `/app`, Flutter in `/mobile`).
5. [`wiki/wiki/environment-setup.md`](wiki/wiki/environment-setup.md) — OrbStack Docker container rules (never install Postgres locally).
6. [`wiki/wiki/skills/three-lens-review/SKILL.md`](wiki/wiki/skills/three-lens-review/SKILL.md) — Template and instructions for posting the 3-Lens Review on GitHub Issues and PRs.

## 🚨 Red Lines
- **NEVER push directly to `master` without review.**
- **NEVER start coding before the GitHub Issue, tests/acceptance criteria, and 3-Lens Review comment have landed.**
- **NEVER install PostgreSQL directly on the host Mac** — always use the PostgreSQL Docker container inside OrbStack.
