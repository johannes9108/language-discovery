# shared/ — Shared Modules

Reusable code and configuration shared across all four projects.

---

## Modules

### `db/`

| File | Description | Used by |
|------|-------------|---------|
| `schema.sql` | PostgreSQL schema: `users`, `products`, `orders`, `scores`, `analytics_events` | A, B, C |
| `sqlite_schema.sql` | SQLite schema: `notes`, `github_stats`, `journal_entries` | D |
| `migrate.sh` | Bash migration runner via `psql` — reads `DATABASE_URL` from env | A, B, C |

### `bash/`

| File | Description | Used by |
|------|-------------|---------|
| `setup.sh` | Checks for required tools: docker, python3, go, cargo, node, julia, R, lua, kotlin, php. Prints ✅/❌ per tool. Installs nothing. | All |
| `common.sh` | Coloured logging helpers: `log_info`, `log_error`, `log_success`. `check_env_var` assertion. | All |

### `python/shared_utils/`

| File | Description | Used by |
|------|-------------|---------|
| `__init__.py` | Package init | A, B, C |
| `http_client.py` | `httpx` wrapper: retry logic, base URL config, `get_json()` / `post_json()` helpers | A, C |
| `auth.py` | JWT helpers using `python-jose`: `create_token(payload)`, `verify_token(token)` | A, C |

### `docker/`

| File | Description | Used by |
|------|-------------|---------|
| `docker-compose.base.yml` | Base services: postgres:16, redis:7-alpine. Network: `polyglot-net`. Named volumes. | A, B, C |
| `.env.example` | Template env vars for database and auth configuration | All |

---

## Environment Variables

| Variable | Description |
|----------|-------------|
| `POSTGRES_USER` | PostgreSQL username |
| `POSTGRES_PASSWORD` | PostgreSQL password |
| `POSTGRES_DB` | Default database name |
| `DATABASE_URL` | Full PostgreSQL connection URL |
| `REDIS_URL` | Redis connection URL |
| `JWT_SECRET` | Secret key for JWT signing |

---

## Usage

```bash
# Source common bash utilities in any script:
source shared/bash/common.sh

# Use Python shared utils:
from shared_utils.http_client import HTTPClient
from shared_utils.auth import create_token, verify_token

# Start base infrastructure:
docker compose -f shared/docker/docker-compose.base.yml up -d

# Run DB migrations:
DATABASE_URL=postgresql://user:pass@localhost/db bash shared/db/migrate.sh
```
