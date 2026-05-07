# Enterprise-Grade URL Shortener Microservice

**Modules Covered:** 5, 6, 7, 8 & 9 Integration  
**Framework:** Django 5.0+ with Django REST Framework (DRF)  
**Timeline:** 15 Working Days

---

## 1. Project Overview

### 1.1 Project Description

Build a production-grade URL shortening service (like Bitly or TinyURL) as a scalable microservice. The project starts with a clean Dockerized foundation and progressively evolves into a complex distributed system:

- **Module 5** → Core + Docker foundation
- **Module 6** → Relational data & ORM
- **Module 7** → Advanced security & RBAC
- **Module 8** → High-performance background tasks
- **Module 9** → Distributed service communication

### 1.2 Core Project Objectives

| Module | Focus | Skills |
|---|---|---|
| Module 5 | Foundational Architecture | Django project structure, Docker, RESTful APIs |
| Module 6 | Data Engineering | Complex schemas, query optimization, Django ORM |
| Module 7 | Security & Access Control | JWT authentication, RBAC |
| Module 8 | Performance Optimization | Redis caching, Celery async processing |
| Module 9 | Microservices Patterns | API Gateway, resilient HTTP, service decoupling |

---

## 2. System Architecture & Data Design

### 2.1 Database Schema

#### A. User Model *(extends `AbstractUser`)*

- `email` → `EmailField` (Unique, Required)
- `is_premium` → `BooleanField` (Default: `False`)
- `tier` → `CharField` (Choices: `Free` | `Premium` | `Admin`)

#### B. URL Model

- `original_url` → `URLField` (validates standard URL formats)
- `short_code` → `CharField` (Unique, Indexed, Max Length: 10)
- `custom_alias` → `CharField` (Nullable, Unique)
- `owner` → `ForeignKey(User, ON DELETE CASCADE)`
- `is_active` → `BooleanField` (Default: `True`)
- `expires_at` → `DateTimeField` (Nullable)
- `title` → `CharField` (Nullable)
- `description` → `CharField` (Nullable)
- `favicon` → `CharField` (Nullable)
- `click_count` → `PositiveIntegerField` (Default: `0`)

#### C. Click (Analytics) Model

- `url` → `ForeignKey(URL, ON DELETE CASCADE)`
- `clicked_at` → `DateTimeField` (auto_now_add=True)
- `ip_address` → `GenericIPAddressField`
- `city` → `CharField` (Nullable)
- `country` → `CharField` (Nullable)
- `user_agent` → `TextField`
- `referrer` → `URLField` (Nullable)

#### D. Tag Model

- `name` → `CharField` (Unique)
- Many-to-Many relationship with URL model

---

## 3. Module 5 Implementation

### Goal

Establish the project foundation, Docker environment, and a Minimum Viable Product (MVP).

### 3.1 Project Structure

Initialize a modular Django project with separate apps:

```
project/
│── core/
│── shortener/
│── api/
```

### 3.2 Configuration Management

Use `python-decouple` or `django-environ` to separate from codebase:

- `SECRET_KEY`
- `DEBUG`
- `DATABASE_URL`

### 3.3 Core Logic (MVP)

- Create a basic `URL` model with `original_url` and `short_code`
- Implement a helper/service to generate random 6-character alphanumeric `short_code` strings

### 3.4 REST API (DRF)

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/urls/` | Accept long URL, return short code |
| `GET` | `/<short_code>/` | Redirect to original URL (HTTP 302) |

Use DRF Serializers for strict URL validation.

### 3.5 Containerization

**Dockerfile:**
- Multi-stage build
- Lightweight Python image

**Docker Compose** — services:
- Django web service
- PostgreSQL database

### 3.6 Documentation

Integrate `drf-yasg` or `drf-spectacular` to auto-generate Swagger/OpenAPI docs.

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
| `GET` | `/api/v1/urls/` | List user URLs (pagination + tag search) |
| `GET` | `/api/v1/urls/{short_code}/` | Retrieve URL details |
| `PUT` | `/api/v1/urls/{short_code}/` | Update URL |
| `DELETE` | `/api/v1/urls/{short_code}/` | Delete or deactivate URL |

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
| Foundation | 1–3 | Module 5 | Docker setup, Django init, MVP endpoints, Swagger docs |
| Data Logic | 4–6 | Module 6 | User/Click models, relationships, migrations, ORM optimization |
| Security | 7–9 | Module 7 | JWT auth, custom permissions, RBAC, rate limiting |
| Scale | 10–12 | Module 8 | Redis caching, Celery integration, async click tracking |
| Integration | 13–15 | Module 9 | URL preview service, final QA, documentation, demo video |

---

## 6. Technical Stack

| Category | Technology |
|---|---|
| Language | Python 3.11+ |
| Framework | Django 5.0+ & DRF |
| Database | PostgreSQL 15+ |
| Authentication | `djangorestframework-simplejwt` |
| Caching | Redis 7+ (`django-redis`) |
| Async Tasks | Celery 5+ (Redis as broker) |
| Containerization | Docker & Docker Compose |
| Documentation | `drf-yasg` / `drf-spectacular` |
| WSGI Server | Gunicorn |

---

## 7. Submission Guidelines

**GitHub Repository** must include:
- `.gitignore`
- `requirements.txt`
- `Dockerfile`
- `docker-compose.yml`
- Atomic commits

**`README.md`** must include:
- Setup instructions & Docker commands
- Architecture diagram
- API endpoint documentation
