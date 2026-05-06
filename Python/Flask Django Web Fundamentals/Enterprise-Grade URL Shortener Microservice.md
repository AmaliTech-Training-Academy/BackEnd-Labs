# Enterprise-Grade URL Shortener Microservice

**Modules Covered:** 5, 6, 7, 8, 9  
**Framework:** Django 5.0+ + Django REST Framework  
**Timeline:** 15 Working Days

---

## 1. Project Overview

### 1.1 Description

Build a production-grade URL shortener (like Bitly/TinyURL) as a scalable microservice.

You will progressively evolve the system:

- **Module 5** → Core + Docker foundation
- **Module 6** → Database & ORM
- **Module 7** → Security (JWT + RBAC)
- **Module 8** → Performance (Redis + Celery)
- **Module 9** → Microservices communication

### 1.2 Core Objectives

- Clean architecture + REST APIs
- Advanced database design & ORM usage
- Secure authentication + RBAC
- High-performance async + caching
- Microservices communication patterns

---

## 2. Database Design (Module 6)

### User Model *(extends `AbstractUser`)*

- `email` — unique, required
- `is_premium` — bool, default `False`
- `tier` — `Free` | `Premium` | `Admin`

### URL Model

- `original_url` — validated URL
- `short_code` — unique, indexed, max 10 chars
- `custom_alias` — optional, unique
- `owner` — FK → User
- `is_active` — bool
- `expires_at` — datetime
- `title`, `description`, `favicon` — optional
- `click_count` — int, default `0`

### Click Model

- `url` — FK → URL
- `clicked_at` — auto timestamp
- `ip_address`
- `city`, `country`
- `user_agent`
- `referrer`

### Tag Model

- `name` — unique
- Many-to-Many → URL

---

## 3. Module Implementation

### Module 5: Foundation + Docker

- Django project structure (modular apps)
- Config via environment variables
- URL shortening MVP:
  - `POST /api/urls/` → create short URL
  - `GET /<short_code>/` → redirect
- `Dockerfile` + `docker-compose` (Postgres)
- Swagger docs (`drf-yasg` / `spectacular`)

### Module 6: Data + ORM

- Extend User model
- Add Click + Tag relationships
- Custom managers:
  - `active_urls()`
  - `expired_urls()`
  - `popular_urls()`
- Query optimization:
  - `select_related` (FK)
  - `prefetch_related` (M2M)
  - `annotate()` for analytics
- Indexing on: `short_code`, `created_at`

### Module 7: Auth + RBAC

- JWT auth (`simplejwt`)
- Endpoints: `register`, `login`, `refresh`
- Permissions: `IsOwnerOrReadOnly`
- Business logic:

  | Tier | Limits |
  |---|---|
  | Free | Max 10 URLs, no custom alias |
  | Premium | Unlimited URLs, custom aliases, analytics access |

- Rate limiting on login endpoint

### Module 8: Performance

- **Redis caching:**
  - Check cache before DB on redirect
  - Cache invalidation on update
- **Celery async tasks:**
  - `track_click_task.delay(...)`
- **Celery Beat:**
  - Cleanup expired URLs
- **Logging:**
  - Structured logs (JSON)
- **Health endpoint:**
  - `/health` — DB + Redis check

### Module 9: Microservices

- **URL Preview Service:**
  - Fetch title, description, favicon
- **HTTP communication:**
  - `httpx` / `requests`
- **Resilience:**
  - Retries with backoff
  - Circuit breaker *(optional)*
- **API Versioning:** `/api/v1/`
- **CORS setup**

---

## 4. API Endpoints

### Auth

```
POST   /api/v1/auth/register/
POST   /api/v1/auth/login/
POST   /api/v1/auth/refresh/
```

### URL Management

```
POST   /api/v1/urls/
GET    /api/v1/urls/
GET    /api/v1/urls/{short_code}/
PUT    /api/v1/urls/{short_code}/
DELETE /api/v1/urls/{short_code}/
```

### Public

```
GET    /{short_code}/   →   redirect (302/301)
```

### Analytics *(Premium only)*

```
GET    /api/v1/analytics/{short_code}/
```

---

## 5. Roadmap (15 Days)

| Days | Focus | Tasks |
|---|---|---|
| Day 1–3 | Foundation | Docker + Django setup, basic shorten + redirect |
| Day 4–6 | Data Layer | Models + relationships, ORM optimization |
| Day 7–9 | Auth & Security | JWT auth, RBAC + rate limiting |
| Day 10–12 | Performance | Redis caching, Celery async tasks |
| Day 13–15 | Microservices & Finalization | External service integration, final testing + documentation |

---

## 6. Tech Stack

| Technology | Role |
|---|---|
| Python 3.11+ | Core language |
| Django 5 + DRF | Web framework + REST API |
| PostgreSQL | Primary database |
| Redis | Caching layer |
| Celery | Async task queue |
| Docker + Compose | Containerization |
| Gunicorn | WSGI server |
| Swagger (`drf-yasg` / `spectacular`) | API documentation |

---

## 7. Submission Requirements

- GitHub repository
- `requirements.txt`
- `.gitignore`
- Docker setup

`README.md` must include:

- Setup instructions
- Architecture diagram
- API endpoints list

> **Demo video recommended**
