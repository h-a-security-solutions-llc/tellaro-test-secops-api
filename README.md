# SecOps Alert Management API

A FastAPI-based security operations center alert management system.

## Architecture

```
backend/
  app/
    main.py          # FastAPI app + lifespan
    config.py        # Settings via pydantic-settings
    database.py      # SQLAlchemy async engine + sessions
    models/          # SQLAlchemy ORM models
      alert.py       # Alert model
      rule.py        # Detection rule model
      user.py        # User model
    schemas/         # Pydantic request/response schemas
    routers/         # FastAPI route handlers
      alerts.py      # /api/alerts CRUD + search
      rules.py       # /api/rules CRUD
      auth.py        # /api/auth login/register
      health.py      # /health
    services/        # Business logic
      alert_service.py
      rule_engine.py
    middleware/       # Auth, CORS, rate limiting
  tests/
  alembic/           # DB migrations
  requirements.txt
```

## Tech Stack
- Python 3.12+, FastAPI, SQLAlchemy 2.0 (async), SQLite/PostgreSQL
- JWT auth via python-jose
- Alembic for migrations
- pytest + httpx for testing

## Quick Start
```bash
cd backend
pip install -r requirements.txt
uvicorn app.main:app --reload --port 8080
```
