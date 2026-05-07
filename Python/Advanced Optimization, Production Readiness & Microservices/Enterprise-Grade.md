# Enterprise-Grade URL Shortener Microservice

**Modules Covered:** 5, 6, 7, 8 & 9 Integration  
**Framework:** Django 5.0+ with Django REST Framework (DRF)  
**Timeline:** 15 Working Days

---

## 1. Project Overview

### 1.1 Project Description

Build a production-grade URL shortening service (like Bitly or TinyURL) as a scalable microservice. Modules 8 and 9 represent the final evolution of the system, adding:

- **Module 8** → Redis caching, Celery async tasks, structured logging, health checks
- **Module 9** → External service integration, resilient inter-service communication, API gateway patterns

### 1.2 Core Project Objectives

| Module | Focus |
|---|---|
| Module 5 | Foundational Architecture & Docker |
| Module 6 | Data Engineering & ORM |
| Module 7 | Security & Access Control |
| **Module 8** | **Performance Optimization — Redis, Celery, production readiness** |
| **Module 9** | **Microservices — external services, resiliency, API gateway** |

---

## 2. Database Schema

### A. User Model *(extends `AbstractUser`)*

- `email` → `EmailField` (Unique, Required)
- `is_premium` → `BooleanField` (Default: `False`)
- `tier` → `CharField` (Choices: `Free` | `Premium` | `Admin`)

### B. URL Model

- `original_url` → `URLField`
- `short_code` → `CharField` (Unique, Indexed, Max Length: 10)
- `custom_alias` → `CharField` (Nullable, Unique)
- `owner` → `ForeignKey(User, ON DELETE CASCADE)`
- `is_active` → `BooleanField` (Default: `True`)
- `expires_at` → `DateTimeField` (Nullable)
- `title`, `description`, `favicon` → `CharField` (Nullable)
- `click_count` → `PositiveIntegerField` (Default: `0`)

### C. Click (Analytics) Model

- `url` → `ForeignKey(URL, ON DELETE CASCADE)`
- `clicked_at` → `DateTimeField` (auto_now_add=True)
- `ip_address` → `GenericIPAddressField`
- `city`, `country` → `CharField` (Nullable)
- `user_agent` → `TextField`
- `referrer` → `URLField` (Nullable)

### D. Tag Model

- `name` → `CharField` (Unique)
- Many-to-Many relationship with URL model

---

## 3. Module 8 Implementation

### Goal

Prepare the system for high traffic using caching and background workers.

### 3.1 Redis Caching

**Redirect Strategy:**
1. Check Redis first
2. If found → redirect immediately
3. If not found → fetch from DB, then cache result

**Cache Invalidation:**
- Delete cache key whenever a URL is updated

### 3.2 Asynchronous Tasks (Celery)

Use the **write-behind pattern** — do NOT write clicks directly inside views:

```python
track_click_task.delay(url_id, ip_address, user_agent)
```

### 3.3 Periodic Tasks (Celery Beat)

- Nightly cleanup job to archive expired URLs

### 3.4 Logging & Monitoring

- Structured **JSON logging**
- Log: 500 errors and security warnings

### 3.5 Health Endpoint

`GET /health` — verifies:
- Database connectivity
- Redis connectivity

---

## 4. Module 9 Implementation

### Goal

Simulate distributed architecture and integrate external services.

### 4.1 URL Preview Service

Fetch metadata from external URLs:
- `title`
- `description`
- `favicon`

### 4.2 Service Layer

Use `httpx` or `requests` to communicate between services.

Create a **separate Django microservice** for the Preview Service. The main app sends HTTP requests to the Preview Service and stores returned metadata in the URL model.

### 4.3 Resiliency Patterns

| Pattern | Implementation |
|---|---|
| Retries | Exponential backoff on failed requests |
| Circuit Breaker | *(Bonus)* Stop retrying failed domains temporarily |

### 4.4 API Gateway Concepts

- API versioning: `/api/v1/`
- CORS headers configuration

---

## 5. API Endpoint Specifications

### Authentication

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/v1/auth/register/` | Register account |
| `POST` | `/api/v1/auth/login/` | Login & receive JWT |
| `POST` | `/api/v1/auth/refresh/` | Refresh access token |

### URL Operations

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/v1/urls/` | Create short URL |
| `GET` | `/api/v1/urls/` | List URLs (pagination + tag search) |
| `GET` | `/api/v1/urls/{short_code}/` | Retrieve URL details |
| `PUT` | `/api/v1/urls/{short_code}/` | Update URL |
| `DELETE` | `/api/v1/urls/{short_code}/` | Delete or deactivate URL |

### Public Interface

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/{short_code}/` | Redirect (HTTP 302/301) — triggers Redis lookup + async analytics task |

### Analytics *(Premium only)*

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/v1/analytics/{short_code}/` | Time-series + geo-location analytics |

---

## 6. Project Roadmap & Milestones

| Phase | Days | Module | Deliverables |
|---|---|---|---|
| Foundation | 1–3 | Module 5 | Docker setup, MVP endpoints, Swagger docs |
| Data Logic | 4–6 | Module 6 | Models, migrations, managers, ORM optimization |
| Security | 7–9 | Module 7 | JWT auth, RBAC, rate limiting |
| **Scale** | **10–12** | **Module 8** | **Redis caching, Celery integration, async click tracking** |
| **Integration** | **13–15** | **Module 9** | **URL preview service, final QA, documentation, demo video** |

---

## 7. Technical Stack

| Category | Technology |
|---|---|
| Language | Python 3.11+ |
| Framework | Django 5.0+ & DRF |
| Database | PostgreSQL 15+ (`psycopg2-binary`) |
| Authentication | `djangorestframework-simplejwt` |
| Caching | Redis 7+ (`django-redis`) |
| Async Tasks | Celery 5+ (Redis as broker) |
| Containerization | Docker & Docker Compose |
| Documentation | `drf-yasg` / `drf-spectacular` |
| WSGI Server | Gunicorn |

---

## 8. Submission Guidelines

**GitHub Repository** must include:
- `.gitignore`
- `requirements.txt`
- `Dockerfile` & `docker-compose.yml`
- Atomic commits

**`README.md`** must include:
- Setup instructions & Docker commands
- Architecture diagram
- API endpoint documentation

> Good luck! Focus on writing clean, modular, scalable code that you would be proud to deploy to production.
