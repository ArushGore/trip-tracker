---
name: three-lens-review
description: Conducts and posts the mandatory 3-Lens Review (Go SDLC, Product Manager UX, Minimalist Google UI Design) on GitHub Issues and Pull Requests.
---

# 3-Lens Review Skill

Use this skill whenever the user or workflow requests a review on a GitHub Issue or Pull Request in `arushgore/trip-tracker`, or before transitioning from specification/testing to implementation.

## 🚨 Red Line Reminder
- **NEVER push to `master` without review.**
- **NEVER start coding a story before the 3-Lens Review has landed on the Issue.**

## 📋 Review Template

Post the review using `gh issue comment <num> --body ...` and/or `gh pr comment <num> --body ...` with the following structure:

```markdown
## 🔍 3-Lens Review

### 1. ⚙️ Go Engineering & SDLC Lens
- **Monolith & Structure**: [Evaluation of modular monolith fit]
- **In-Memory & Goroutines**: [Evaluation of concurrency, state, channels, safety]
- **Database Persistence**: [Evaluation of Postgres schema/queries inside OrbStack container]
- **Tests & Acceptance Criteria**: [Verification of test coverage before code]

### 2. 🧭 Product Manager Lens (User Experience & Journey)
- **Traveler Value**: [How this helps frequent travelers count days accurately]
- **User Journey & Edge Cases**: [Entry/exit flows, date boundary edge cases]
- **Web (`app`) & Mobile (`mobile`) Parity**: [Confirmation that both surfaces share identical functionality]

### 3. 🎨 UI Designer Lens (Minimalist Google Design Guidelines)
- **Visual Hierarchy & Minimalism**: [Clutter reduction, focus on core day counts]
- **Google Design / Material 3 Alignment**: [Typography, spacing, color tokens, elevation]
- **Cross-Surface Consistency**: [Harmony between HTMX web templates and Flutter widgets]

---
**Verdict**: [APPROVED TO START CODING / APPROVED TO MERGE / CHANGES REQUESTED]
```
