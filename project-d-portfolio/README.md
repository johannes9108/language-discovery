# Project D — Portfolio Site & CLI Tools

A personal developer portfolio website paired with a suite of CLI tools — one per language — all solving the same problem (e.g., fetching GitHub stats) so you can compare idioms directly.

---

## Architecture

```
project-d-portfolio/
├── website/          Next.js portfolio site (deployed to Vercel)
├── cli/
│   ├── python/       argparse CLI
│   ├── go/           cobra CLI
│   ├── rust/         clap CLI
│   ├── julia/        ARGS-based Julia script
│   └── c/            getopt C CLI
├── analysis/         R script — fetches & visualises GitHub stats
├── config/           Neovim Lua config stub
└── scripts/          setup.sh, install.sh
```

---

## Language Roles

| Language | Component | What you learn |
|----------|-----------|----------------|
| TypeScript (Next.js) | `website/` | App Router, MDX blog, static generation, API routes |
| Python | `cli/python/` | argparse, `requests`, `rich` for terminal output |
| Go | `cli/go/` | cobra CLI framework, HTTP client, JSON parsing |
| Rust | `cli/rust/` | clap v4, `reqwest`, `serde_json`, error handling |
| Julia | `cli/julia/` | ARGS, HTTP.jl, JSON3.jl, scripting vs module pattern |
| C | `cli/c/` | getopt, libcurl, string manipulation, Makefile |
| R | `analysis/` | httr2 / gh package, ggplot2 timeline chart |
| Bash | `scripts/` | Portable installer patterns, OS detection, `set -euo pipefail` |
| Lua | `config/` | Neovim plugin config, table-based configuration DSL |

---

## The CLI Challenge

All five CLI tools do **exactly the same thing**:

1. Accept a GitHub username as argument (`--user <name>` or positional)
2. Fetch the user's public repos from the GitHub API
3. Print a formatted table: name | stars | language | last updated
4. Optionally export to JSON (`--output file.json`)

Implementing this in each language lets you directly compare:
- Argument parsing libraries
- HTTP client ergonomics
- JSON deserialization patterns
- Error handling idioms
- Build/run workflows

---

## How to Run

### Next.js website
```bash
cd website && npm install && npm run dev
# http://localhost:3000
```

### CLI tools — all accept the same flags
```bash
# Python
cd cli/python && python main.py --user johndoe

# Go
cd cli/go && go run . --user johndoe

# Rust
cd cli/rust && cargo run -- --user johndoe

# Julia
cd cli/julia && julia main.jl --user johndoe

# C
cd cli/c && make && ./github-stats --user johndoe
```

### R analysis
```bash
cd analysis && Rscript analysis.R johndoe
```

---

## Learning Goals

1. **Next.js** — static site generation, MDX, ISR (Incremental Static Regeneration), deployment
2. **Python CLI** — `argparse`, `rich` tables, `httpx`/`requests`, scripting best practices
3. **Go CLI** — `cobra` framework, struct tags for JSON, idiomatic error wrapping
4. **Rust CLI** — `clap` derive macros, `reqwest` async, `serde` derive, `anyhow` errors
5. **Julia** — script vs package structure, HTTP.jl, metaprogramming basics
6. **C** — `getopt_long`, manual JSON parsing or `cJSON` library, Makefile compilation targets
7. **R** — functional data manipulation (dplyr), HTTP API access (httr2), ggplot2 timeline
8. **Bash** — robust scripting with `set -euo pipefail`, OS detection, coloured output
9. **Lua** — Neovim config DSL, `require`, lazy-loading plugins

---

## Files to Implement

See [`PLAN.md`](../PLAN.md) for the full scaffold checklist.

```
project-d-portfolio/
├── README.md                     ← this file
├── website/
│   ├── package.json
│   └── pages/index.tsx
├── cli/
│   ├── python/main.py
│   ├── go/
│   │   ├── main.go
│   │   └── go.mod
│   ├── rust/
│   │   ├── src/main.rs
│   │   └── Cargo.toml
│   ├── julia/main.jl
│   └── c/
│       ├── main.c
│       └── Makefile
├── analysis/
│   └── analysis.R
├── config/
│   └── init.lua
└── scripts/
    ├── setup.sh
    └── install.sh
```
