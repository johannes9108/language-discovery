# language-discovery 🌐

A **polyglot learning monorepo** for exploring 10+ programming languages across 4 real-world projects. Each project solves a different domain problem and is intentionally built with multiple languages to force you to compare idioms, toolchains, and ecosystems side-by-side.

---

## Projects at a Glance

| Project | Domain | Primary Languages |
|---------|--------|-------------------|
| [A — Analytics Platform](./project-a-analytics/) | Full-stack data analytics | Go, Python, R, Julia, Rust, TypeScript, Lua |
| [B — Multiplayer Game](./project-b-game/) | Real-time game backend | Go, Rust (WASM), C, Python, Kotlin, TypeScript |
| [C — E-Commerce](./project-c-ecommerce/) | Microservices storefront | Go, Kotlin, Python, Rust, PHP, Scala, C#, TypeScript |
| [D — Portfolio / CLI](./project-d-portfolio/) | Personal site + dev tools | TypeScript (Next.js), Python, Go, Rust, Julia, Bash, R, C, Lua |

---

## Monorepo Structure

```
language-discovery/
├── README.md               ← You are here
├── Makefile                ← Root automation
├── PLAN.md                 ← Full scaffold checklist
├── shared/                 ← Reused across all projects
│   ├── README.md
│   ├── db/                 ← SQL schemas + migration script
│   ├── bash/               ← setup.sh, common.sh utilities
│   ├── python/             ← shared_utils (http_client, auth)
│   └── docker/             ← docker-compose.base.yml, .env.example
├── project-a-analytics/
├── project-b-game/
├── project-c-ecommerce/
└── project-d-portfolio/
```

---

## Language → Project Mapping

| Language | Project A | Project B | Project C | Project D |
|----------|:---------:|:---------:|:---------:|:---------:|
| Go | Gateway | WS Server | Gateway | CLI tool |
| Python | FastAPI | Leaderboard API | Recommendation svc | CLI tool, R analysis |
| TypeScript/React | Frontend | Game client | Next.js storefront | Next.js site |
| Rust | CSV processor | WASM physics | Payment svc | CLI tool |
| R | Data analysis | — | — | Analytics script |
| Julia | Matrix compute | — | — | CLI tool |
| C | — | Game engine | — | CLI tool |
| Kotlin | — | State manager | Order service | Stub |
| PHP | — | — | Catalog svc | — |
| Scala | — | — | Event consumer | — |
| C# | — | — | Dashboard | — |
| Lua | Config | — | — | Neovim config |
| Bash | shared/bash | scripts/ | scripts/ | install scripts |

---

## Suggested Learning Order (6-Month Timeline)

| Month | Focus | What to build |
|-------|-------|---------------|
| 1 | Bash + Go | `shared/bash/`, Project A gateway |
| 2 | Python + FastAPI | Project A API, shared Python utils |
| 3 | Rust | Project A processor, Project B WASM physics |
| 4 | TypeScript + React | Project A frontend, Project D Next.js site |
| 5 | JVM (Kotlin + Scala) + PHP | Project C order-service, catalog, consumer |
| 6 | R + Julia + C + Lua | Project A analysis, Project B engine, Lua config |

---

## Getting Started

### Prerequisites

Run the environment checker:
```bash
bash shared/bash/setup.sh
```

### Quick commands (via Makefile)

```bash
make setup      # validate environment
make start-a    # start Project A
make start-b    # start Project B
make start-c    # start Project C
make start-d    # start Project D
make build-all  # build all projects
make clean      # remove build artefacts
make help       # list all targets
```

### Database

Copy and edit the example env file, then run migrations:
```bash
cp shared/docker/.env.example .env
# edit .env with your credentials
bash shared/db/migrate.sh
```

---

## Shared Modules

See [`shared/README.md`](./shared/README.md) for a full description of each shared module.