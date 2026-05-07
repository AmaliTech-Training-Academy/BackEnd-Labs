# Enterprise-Grade URL Shortener Microservice

**Modules Covered:** 5, 6, 7, 8 & 9 Integration  
**Framework:** Django 5.0+ with Django REST Framework (DRF)  
**Timeline:** 15 Working Days

---

## 1. Project Overview

### 1.1 Project Description

Build a production-grade URL shortening service (like Bitly or TinyURL) as a scalable microservice. Starting from the Module 5 foundation, Module 6 expands the system with:

- User ownership and tiers
- Tagging and categorization
- Click analytics tracking
- Efficient database access and query optimization

### 1.2 Core Project Objectives

| Module | Focus |
|---|---|
| Module 5 | Foundational Architecture & Docker |
| **Module 6** | **Data Engineering — schemas, ORM, query optimization** |
| Module 7 | Security & Access Control |
| Module 8 | Performance Optimization |
| Module 9 | Microservices Patterns |

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

## 3. Module 6 Implementation

### Goal

Expand the data model to support users, relationships, and deep analytics. Focus on efficient database access and query optimization.

### 3.1 Advanced Modeling

**User Model** — extend `AbstractUser`, add `is_premium` and `tier`

**URL Model enhancements** — add `owner`, `click_count`, `is_active`, `expires_at`

**Click Model** — track `ip_address`, `user_agent`, `country`, `city`, `referrer`

**Tags** — implement Many-to-Many relationships (e.g., `Marketing`, `Social`)

### 3.2 Database Migrations

- Manage all schema changes using proper Django migrations
- Create a **data migration** to seed default tags

### 3.3 Custom Managers & QuerySets

Implement `URLManager` with:

- `active_urls()` — returns only active, non-expired URLs
- `expired_urls()` — returns URLs past their `expires_at`
- `popular_urls()` — returns URLs ordered by `click_count`

### 3.4 Query Optimization

**N+1 Problem Prevention:**
- `select_related()` → for `owner` (ForeignKey)
- `prefetch_related()` → for `tags` (Many-to-Many)

**Database Indexing:**
- Index on `short_code`
- Index on `created_at`

**Aggregation with `annotate()`:**
- Total clicks per country
- Other analytics computed directly in SQL

---

## 4. API Endpoint Specifications

### Authentication

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/v1/auth/register/` | Create new account |
| `POST` | `/api/v1/auth/login/` | Returns Access/Refresh JWT |
| `POST` | `/api/v1/auth/refresh/` | Generate new Access Token |

### URL Operations

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/v1/urls/` | Create short URL |
| `GET` | `/api/v1/urls/` | List user URLs |
| `GET` | `/api/v1/urls/{short_code}/` | Retrieve URL details |
| `PUT` | `/api/v1/urls/{short_code}/` | Update URL |
| `DELETE` | `/api/v1/urls/{short_code}/` | Delete or deactivate |

### Public Interface

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/{short_code}/` | Redirect (HTTP 302/301) |

### Analytics *(Premium only)*

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/v1/analytics/{short_code}/` | Time-series + geo analytics |

---

## 5. Project Roadmap & Milestones

| Phase | Days | Module | Deliverables |
|---|---|---|---|
| Foundation | 1–3 | Module 5 | Docker setup, MVP endpoints, Swagger docs |
| **Data Logic** | **4–6** | **Module 6** | **User/Click models, relationships, migrations, managers, N+1 optimization** |
| Security | 7–9 | Module 7 | JWT auth, RBAC, rate limiting |
| Scale | 10–12 | Module 8 | Redis caching, Celery async tasks |
| Integration | 13–15 | Module 9 | URL preview service, QA, documentation |

---

## 6. Technical Stack

| Category | Technology |
|---|---|
| Language | Python 3.11+ |
| Framework | Django 5.0+ & DRF |
| Database | PostgreSQL 15+ (`psycopg2-binary`) |
| Authentication | `djangorestframework-simplejwt` |
| Caching | Redis 7+ |
| Async Tasks | Celery 5+ |
| Containerization | Docker & Docker Compose |
| Documentation | `drf-yasg` / `drf-spectacular` |
| WSGI Server | Gunicorn |

---

## 7. Submission Guidelines

**GitHub Repository** must include:
- `.gitignore`
- `requirements.txt`
- `Dockerfile` & `docker-compose.yml`
- Atomic commits

**`README.md`** must include:
- Setup instructions & Docker commands
- Architecture diagram
- API endpoint documentation
