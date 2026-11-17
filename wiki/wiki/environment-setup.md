---
title: Build Machine & Local Environment
tags: [environment, mac, orbstack, postgres, docker, flutter, go, homebrew]
summary: Primary macOS build machine configuration, SDK versions, and OrbStack Docker setup.
---

# Build Machine & Local Environment

This macOS machine (`darwin/arm64`) is the **primary build machine** for Trip Tracker.

> [!IMPORTANT]
> **PostgreSQL Rule**: Never install or run PostgreSQL directly on macOS (e.g. via `brew install postgresql`). PostgreSQL **must** always run inside a Docker container managed by **OrbStack**.

---

## 🛠️ Required Toolchain

1. **Homebrew**: Kept up to date (`brew update && brew upgrade`) for managing system packages.
2. **Go SDK**: Installed via Homebrew (`/opt/homebrew/bin/go`, version `go1.27.4 darwin/arm64`) for compiling and testing `/app`.
3. **Flutter SDK**: Installed at `/opt/homebrew/bin/flutter` (stable channel, version `3.50.0`, Dart `3.14.0`) for building and testing `/mobile`.
4. **OrbStack**: Installed via Homebrew Cask (`brew install --cask orbstack`). Provides the lightweight container runtime (`docker`, `docker-compose`, `orb`) for running:
   - **PostgreSQL container** (`postgres:17-alpine`, container name `trip-tracker-postgres`, port `5432`)
   - **Trip Tracker `/app` container** (port-forwarded locally to the host browser and mobile simulator on a non-SSL port such as `8080`).

---

## 🐳 Container Operations (OrbStack)

- **Start Local Stack**:
  ```bash
  docker-compose up -d
  ```
- **Verify Containers**:
  ```bash
  docker ps
  ```
- **Local Web Access**: Open `http://localhost:8080` in the browser.
- **Mobile Dev Connection**: Point the Flutter app's dev base URL to the local non-SSL port (`http://localhost:8080`), while production builds use `https://<prod-host>:443`.
