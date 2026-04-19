# Project C — Microservices E-Commerce Platform

A fully decomposed e-commerce backend where every microservice is written in a different language — deliberately maximising polyglot exposure.

---

## Architecture

```
 Browser / Mobile
       │ HTTPS
       ▼
 Go API Gateway  :8080
       │
  ┌────┴────────────────────────────────────────────┐
  │              Internal services                   │
  │                                                  │
  ▼                ▼              ▼          ▼       │
Kotlin          Python         Rust       PHP        │
Order svc       Recommend.     Payment    Catalog    │
:8081           svc :8082      svc :8083  svc :8084  │
  │                                                  │
  ▼                                                  │
Scala Kafka consumer  (order events → analytics DB)  │
                                                     │
C# Blazor Dashboard  :5000   ◀── admin UI            │
                                                     │
Next.js Storefront  :3000    ◀── customer UI         │
  └────────────────────────────────────────────────-─┘
```

---

## Language Roles

| Language | Service | What you learn |
|----------|---------|----------------|
| Go | `gateway/` | API gateway pattern, request routing, middleware chaining |
| Kotlin | `order-service/` | Spring Boot (or Ktor), JPA/exposed ORM, dependency injection |
| Python | `recommendation/` | Collaborative filtering stub, pandas, scikit-learn |
| Rust | `payment/` | Axum web framework, async Rust, error handling with `thiserror` |
| PHP | `catalog/` | Slim framework, PDO, REST API conventions |
| Scala | `consumer/` | Kafka consumer with Akka Streams or fs2-kafka |
| C# | `dashboard/` | ASP.NET Core / Blazor, EF Core, SignalR for live updates |
| TypeScript | `storefront/` | Next.js App Router, SSR vs SSG, API routes |

---

## How to Run

### Full stack (Docker)
```bash
cp shared/docker/.env.example .env
docker compose up --build
# Storefront:  http://localhost:3000
# Gateway:     http://localhost:8080
# Dashboard:   http://localhost:5000
```

### Individual services
```bash
# Go gateway
cd gateway && go run .

# Kotlin order service
cd order-service && ./gradlew bootRun

# Python recommendation
cd recommendation && pip install -r requirements.txt && uvicorn main:app --reload

# Rust payment service
cd payment && cargo run

# PHP catalog
cd catalog && composer install && php -S localhost:8084 index.php

# Scala consumer
cd consumer && sbt run

# C# dashboard
cd dashboard && dotnet run

# Next.js storefront
cd storefront && npm install && npm run dev
```

---

## Learning Goals

1. **Go gateway** — understand API gateway pattern: authentication, rate-limiting, path rewriting
2. **Kotlin/JVM** — Spring Boot conventions, build tooling (Gradle), type-safe DSLs
3. **Rust async** — `tokio` runtime, `axum` handlers, `Result`-based error propagation
4. **PHP** — legacy-aware web patterns, Composer dependency management, PDO
5. **Scala** — functional streaming, type classes, sbt build tool
6. **C#** — .NET ecosystem, Blazor components, LINQ, async/await (C# flavour)
7. **Next.js** — modern React meta-framework, file-based routing, server components

---

## Files to Implement

See [`PLAN.md`](../PLAN.md) for the full scaffold checklist.

```
project-c-ecommerce/
├── README.md                      ← this file
├── docker-compose.yml
├── gateway/
│   ├── main.go
│   └── go.mod
├── order-service/
│   ├── src/main/kotlin/OrderService.kt
│   └── build.gradle.kts
├── recommendation/
│   ├── main.py
│   └── requirements.txt
├── payment/
│   ├── src/main.rs
│   └── Cargo.toml
├── catalog/
│   ├── index.php
│   └── composer.json
├── consumer/
│   ├── src/main/scala/EventConsumer.scala
│   └── build.sbt
├── dashboard/
│   ├── Program.cs
│   └── dashboard.csproj
├── storefront/
│   ├── package.json
│   └── pages/index.tsx
└── scripts/
    └── run.sh
```
