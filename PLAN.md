# Scaffold Plan — language-discovery

This document tracks every file that needs to be created for the full polyglot monorepo scaffold.
Check off items as you implement them.

---

## Root

- [ ] `README.md` — comprehensive overview ✅ (already updated)
- [ ] `Makefile` — `setup`, `start-a/b/c/d`, `build-all`, `clean`, `help` targets

---

## `shared/`

- [ ] `shared/README.md` ✅ (see below)
- [ ] `shared/db/schema.sql` — PostgreSQL: `users`, `products`, `orders`, `scores`, `analytics_events`
- [ ] `shared/db/sqlite_schema.sql` — SQLite: `notes`, `github_stats`, `journal_entries`
- [ ] `shared/db/migrate.sh` — runs migrations via `psql`, reads `DATABASE_URL`
- [ ] `shared/bash/setup.sh` — checks docker, python3, go, cargo, node, julia, R, lua, kotlin, php
- [ ] `shared/bash/common.sh` — `log_info`, `log_error`, `log_success`, `check_env_var`
- [ ] `shared/python/shared_utils/__init__.py`
- [ ] `shared/python/shared_utils/http_client.py` — `httpx` wrapper with retry + JSON helpers
- [ ] `shared/python/shared_utils/auth.py` — JWT helpers: `create_token`, `verify_token`
- [ ] `shared/docker/docker-compose.base.yml` — postgres:16, redis:7-alpine, `polyglot-net`
- [ ] `shared/docker/.env.example`

---

## `project-a-analytics/` — Full-Stack Data Analytics Platform

Languages: **Go · Python · R · Julia · Rust · TypeScript/React · Lua**

- [ ] `project-a-analytics/README.md` ✅ (see below)
- [ ] `project-a-analytics/docker-compose.yml` — extends base, adds gateway/api/frontend
- [ ] `project-a-analytics/gateway/main.go` — reverse proxy, `/health`, logger middleware
- [ ] `project-a-analytics/gateway/go.mod` — `module analytics-gateway`, `go 1.22`
- [ ] `project-a-analytics/api/main.py` — FastAPI: `/health`, `/data`, `/predict`
- [ ] `project-a-analytics/api/requirements.txt` — fastapi, uvicorn, asyncpg, pandas, scikit-learn, python-jose, httpx
- [ ] `project-a-analytics/analysis/r/analysis.R` — RPostgres query + ggplot2 chart
- [ ] `project-a-analytics/analysis/julia/compute.jl` — matrix multiply benchmark + eigenvalues
- [ ] `project-a-analytics/processor/src/main.rs` — clap CLI: read CSV, print stats, write cleaned
- [ ] `project-a-analytics/processor/Cargo.toml` — clap, csv, serde, serde_json
- [ ] `project-a-analytics/frontend/package.json` — React + TypeScript + Vite + D3 + axios
- [ ] `project-a-analytics/frontend/src/App.tsx` — fetch `/api/data`, table + D3 bar chart
- [ ] `project-a-analytics/frontend/src/main.tsx`
- [ ] `project-a-analytics/frontend/tsconfig.json`
- [ ] `project-a-analytics/config/config.lua` — Lua config (DB URL, feature flags)
- [ ] `project-a-analytics/scripts/run.sh`

---

## `project-b-game/` — Real-Time Multiplayer Game

Languages: **TypeScript · Go · Rust (WASM) · C · Python · Kotlin**

- [ ] `project-b-game/README.md` ✅ (see below)
- [ ] `project-b-game/docker-compose.yml`
- [ ] `project-b-game/client/package.json` — TypeScript game client (canvas/WebSocket)
- [ ] `project-b-game/client/src/main.ts` — connects to WS server, renders game loop
- [ ] `project-b-game/client/src/state.ts` — Kotlin-style state manager (TypeScript class)
- [ ] `project-b-game/server/main.go` — Go WebSocket server (gorilla/websocket)
- [ ] `project-b-game/server/go.mod`
- [ ] `project-b-game/physics/src/lib.rs` — Rust WASM physics: gravity, collision detection
- [ ] `project-b-game/physics/Cargo.toml` — wasm-bindgen, getrandom
- [ ] `project-b-game/engine/main.c` — C game engine: entity/component structs, update loop
- [ ] `project-b-game/engine/Makefile`
- [ ] `project-b-game/leaderboard/main.py` — FastAPI leaderboard API with asyncpg
- [ ] `project-b-game/leaderboard/requirements.txt`
- [ ] `project-b-game/state-manager/StateManager.kt` — Kotlin state manager stub
- [ ] `project-b-game/scripts/run.sh`

---

## `project-c-ecommerce/` — Microservices E-Commerce Platform

Languages: **Go · Kotlin · Python · Rust · PHP · Scala · C# · TypeScript (Next.js)**

- [ ] `project-c-ecommerce/README.md` ✅ (see below)
- [ ] `project-c-ecommerce/docker-compose.yml`
- [ ] `project-c-ecommerce/gateway/main.go` — Go API gateway
- [ ] `project-c-ecommerce/gateway/go.mod`
- [ ] `project-c-ecommerce/order-service/src/main/kotlin/OrderService.kt`
- [ ] `project-c-ecommerce/order-service/build.gradle.kts`
- [ ] `project-c-ecommerce/recommendation/main.py` — Python recommendation engine
- [ ] `project-c-ecommerce/recommendation/requirements.txt`
- [ ] `project-c-ecommerce/payment/src/main.rs` — Rust payment processor
- [ ] `project-c-ecommerce/payment/Cargo.toml`
- [ ] `project-c-ecommerce/catalog/index.php` — PHP catalog service (Slim or vanilla)
- [ ] `project-c-ecommerce/catalog/composer.json`
- [ ] `project-c-ecommerce/consumer/src/main/scala/EventConsumer.scala`
- [ ] `project-c-ecommerce/consumer/build.sbt`
- [ ] `project-c-ecommerce/dashboard/Program.cs` — C# Blazor/ASP.NET dashboard
- [ ] `project-c-ecommerce/dashboard/dashboard.csproj`
- [ ] `project-c-ecommerce/storefront/package.json` — Next.js storefront
- [ ] `project-c-ecommerce/storefront/pages/index.tsx`
- [ ] `project-c-ecommerce/scripts/run.sh`

---

## `project-d-portfolio/` — Personal Portfolio + CLI Tools

Languages: **TypeScript (Next.js) · Python · Go · Rust · Julia · Bash · R · C · Lua**

- [ ] `project-d-portfolio/README.md` ✅ (see below)
- [ ] `project-d-portfolio/website/package.json` — Next.js site
- [ ] `project-d-portfolio/website/pages/index.tsx`
- [ ] `project-d-portfolio/cli/python/main.py` — Python CLI (argparse)
- [ ] `project-d-portfolio/cli/go/main.go` — Go CLI (cobra)
- [ ] `project-d-portfolio/cli/go/go.mod`
- [ ] `project-d-portfolio/cli/rust/src/main.rs` — Rust CLI (clap)
- [ ] `project-d-portfolio/cli/rust/Cargo.toml`
- [ ] `project-d-portfolio/cli/julia/main.jl` — Julia CLI script
- [ ] `project-d-portfolio/cli/c/main.c` — C CLI (getopt)
- [ ] `project-d-portfolio/cli/c/Makefile`
- [ ] `project-d-portfolio/analysis/analysis.R` — R GitHub stats analysis
- [ ] `project-d-portfolio/config/init.lua` — Neovim Lua config stub
- [ ] `project-d-portfolio/scripts/setup.sh` — install all dependencies
- [ ] `project-d-portfolio/scripts/install.sh` — OS-level install helper

---

## GitHub Actions (`.github/workflows/`)

- [ ] `.github/workflows/project-a.yml` — Go build, Python lint/test, Rust cargo build
- [ ] `.github/workflows/project-b.yml` — Go build, Rust WASM build, Python lint
- [ ] `.github/workflows/project-c.yml` — Go build, Kotlin/Gradle build, Rust build, PHP composer
- [ ] `.github/workflows/project-d.yml` — Next.js build, Go build, Rust build
