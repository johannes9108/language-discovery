# Project A — Full-Stack Data Analytics Platform

A multi-language data analytics platform demonstrating how different languages tackle data ingestion, processing, API serving, and visualisation.

---

## Architecture

```
                 ┌──────────────────────────────────────────────┐
 Browser ──────▶ │  Go Gateway  :8080                           │
                 │  (reverse proxy + logger middleware)          │
                 └────────────────────┬─────────────────────────┘
                                      │ /api/*
                 ┌────────────────────▼─────────────────────────┐
                 │  Python FastAPI  :8000                        │
                 │  /health  /data  /predict                     │
                 └──────────┬───────────────────────────────────┘
                            │
               ┌────────────┼────────────────┐
               ▼            ▼                ▼
          PostgreSQL    R analysis      Julia compute
          (asyncpg)    (RPostgres +    (matrix/eigen)
                        ggplot2)
               ▲
               │
    Rust CSV Processor (CLI — offline)
```

---

## Language Roles

| Language | Component | What you learn |
|----------|-----------|----------------|
| Go | `gateway/` | HTTP reverse proxy, middleware, net/http |
| Python | `api/` | FastAPI, asyncpg, async/await, scikit-learn |
| R | `analysis/r/` | RPostgres, ggplot2, data frames |
| Julia | `analysis/julia/` | LinearAlgebra, benchmarking, REPL workflow |
| Rust | `processor/` | clap, csv crate, serde, ownership with file IO |
| TypeScript | `frontend/` | React, D3.js, Vite, component architecture |
| Lua | `config/` | Configuration scripting, tables |

---

## How to Run

### Full stack (Docker)
```bash
cp shared/docker/.env.example .env
docker compose up --build
# Gateway:  http://localhost:8080
# Frontend: http://localhost:5173
```

### Gateway only
```bash
cd gateway && go run .
```

### API only
```bash
cd api && pip install -r requirements.txt && uvicorn main:app --reload
```

### Rust CSV processor
```bash
cd processor && cargo run -- --file path/to/data.csv
```

### R analysis
```bash
cd analysis/r && Rscript analysis.R
```

### Julia compute
```bash
cd analysis/julia && julia compute.jl
```

---

## Learning Goals

1. **Go** — understand the standard library HTTP stack, writing middleware, reverse proxying
2. **Python async** — `async def`, `await`, lifespan events, database connection pools
3. **Rust ownership** — borrow checker in practice with file/stream IO
4. **R** — connect to a real DB, wrangle data frames, produce publication-quality plots
5. **Julia** — high-performance numeric computing, compare speed vs Python/R
6. **TypeScript + React** — component lifecycle, D3 integration, API fetching patterns
7. **Lua** — embedded scripting for configuration, table syntax

---

## Files to Implement

See [`PLAN.md`](../PLAN.md) for the full scaffold checklist.

```
project-a-analytics/
├── README.md                    ← this file
├── docker-compose.yml
├── gateway/
│   ├── main.go
│   └── go.mod
├── api/
│   ├── main.py
│   └── requirements.txt
├── analysis/
│   ├── r/analysis.R
│   └── julia/compute.jl
├── processor/
│   ├── src/main.rs
│   └── Cargo.toml
├── frontend/
│   ├── package.json
│   ├── tsconfig.json
│   └── src/
│       ├── App.tsx
│       └── main.tsx
├── config/
│   └── config.lua
└── scripts/
    └── run.sh
```
