# Project B — Real-Time Multiplayer Game

A browser-based multiplayer game demonstrating WebSocket communication, WASM physics, and a native C engine — all wired together.

---

## Architecture

```
 Browser (TypeScript canvas client)
   │  WebSocket
   ▼
 Go WebSocket Server  :9000
   │  game events
   ├──▶ Rust WASM Physics  (loaded in browser)
   │      gravity, collision detection
   │
   ├──▶ C Game Engine  (server-side logic / offline sim)
   │      entity/component structs, update loop
   │
   └──▶ Python Leaderboard API  :8001
           FastAPI + PostgreSQL

 Kotlin StateManager  (shared state abstraction — JVM or transpiled)
```

---

## Language Roles

| Language | Component | What you learn |
|----------|-----------|----------------|
| TypeScript | `client/` | DOM canvas API, WebSocket client, game loop, state management |
| Go | `server/` | goroutines, channels, gorilla/websocket, concurrent game rooms |
| Rust | `physics/` | WASM compilation, wasm-bindgen, unsafe-free physics math |
| C | `engine/` | Structs, pointers, manual memory, Makefile compilation |
| Python | `leaderboard/` | FastAPI, asyncpg, simple REST CRUD |
| Kotlin | `state-manager/` | Data classes, sealed classes, idiomatic JVM style |

---

## How to Run

### Full stack (Docker)
```bash
cp shared/docker/.env.example .env
docker compose up --build
# Game client: http://localhost:3000
# WS Server:   ws://localhost:9000
# Leaderboard: http://localhost:8001
```

### Go WebSocket server
```bash
cd server && go run .
```

### Rust WASM physics (build)
```bash
cd physics && wasm-pack build --target web
```

### C engine
```bash
cd engine && make
./engine
```

### Python leaderboard API
```bash
cd leaderboard && pip install -r requirements.txt && uvicorn main:app --reload
```

---

## Learning Goals

1. **Go concurrency** — goroutines and channels for managing multiple game rooms simultaneously
2. **Rust + WASM** — compile Rust to WebAssembly, call from TypeScript, understand the boundary
3. **C fundamentals** — structs, function pointers, `malloc`/`free`, writing a Makefile from scratch
4. **TypeScript game loop** — `requestAnimationFrame`, canvas 2D API, managing WebSocket state
5. **Kotlin idioms** — data classes, `when` expressions, sealed class hierarchies
6. **Python CRUD API** — async database access, Pydantic models, route handlers

---

## Files to Implement

See [`PLAN.md`](../PLAN.md) for the full scaffold checklist.

```
project-b-game/
├── README.md                    ← this file
├── docker-compose.yml
├── client/
│   ├── package.json
│   └── src/
│       ├── main.ts
│       └── state.ts
├── server/
│   ├── main.go
│   └── go.mod
├── physics/
│   ├── src/lib.rs
│   └── Cargo.toml
├── engine/
│   ├── main.c
│   └── Makefile
├── leaderboard/
│   ├── main.py
│   └── requirements.txt
├── state-manager/
│   └── StateManager.kt
└── scripts/
    └── run.sh
```
