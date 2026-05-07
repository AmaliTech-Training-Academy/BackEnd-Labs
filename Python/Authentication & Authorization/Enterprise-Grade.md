# Enterprise-Grade URL Shortener Microservice


**Modules Covered:** 5, 6, 7, 8 & 9 Integration  
**Framework:** Django 5.0+ with Django REST Framework (DRF)  
**Timeline:** 15 Working Days

---

## 1. Project Overview

### 1.1 Project Description

Build a production-grade URL shortening service (like Bitly or TinyURL) as a scalable microservice. Building on Modules 5 and 6, Module 7 secures the platform by introducing:

- Industry-standard JWT authentication
- Role-Based Access Control (RBAC)
- Tiered user permissions (Free vs Premium)
- Rate limiting and security best practices

### 1.2 Core Project Objectives

| Module | Focus |
|---|---|
| Module 5 | Foundational Architecture & Docker |
| Module 6 | Data Engineering & ORM |
| **Module 7** | **Security & Access Control — JWT, RBAC, tiered logic** |
| Module 8 | Performance Optimization |
| Module 9 | Microservices Patterns |

---

## 2. Database Schema

### A. User Model *(extends `AbstractUser`)*

- `email` → `EmailField(unique=True, required=True)`
- `is_premium` → `BooleanField(default=False)`
- `tier` → `CharField(choices=['Free', 'Premium', 'Admin'])`

### B. URL Model

- `original_url` → `URLField`
- `short_code` → `CharField(unique=True, indexed=True, max_length=10)`
- `custom_alias` → `CharField(nullable=True, unique=True)`
- `owner` → `ForeignKey(User, on_delete=CASCADE)`
- `is_active` → `BooleanField(default=True)`
- `expires_at` → `DateTimeField(nullable=True)`
- `title`, `description`, `favicon` → `CharField(nullable=True)`
- `click_count` → `PositiveIntegerField(default=0)`

### C. Click (Analytics) Model

- `url` → `ForeignKey(URL, on_delete=CASCADE)`
- `clicked_at` → `DateTimeField(auto_now_add=True)`
- `ip_address` → `GenericIPAddressField`
- `city`, `country` → `CharField(nullable=True)`
- `user_agent` → `TextField`
- `referrer` → `URLField(nullable=True)`

### D. Tag Model

- `name` → `CharField(unique=True)`
- Many-to-Many relationship with URL model

---

## 3. Module 7 Implementation

### Goal

Secure the application and implement business rules based on user roles.

### 3.1 JWT Authentication

Install `djangorestframework-simplejwt` and implement endpoints:

| Method | Endpoint | Description |
|---|---|---|
| `POST` | `/api/v1/auth/register/` | Create new user account |
| `POST` | `/api/v1/auth/login/` | Returns Access + Refresh JWT |
| `POST` | `/api/v1/auth/refresh/` | Generate new Access Token |

### 3.2 Role-Based Access Control (RBAC)

**Custom Permission:**
- `IsOwnerOrReadOnly` → users cannot edit or delete URLs they do not own

**Tier Logic:**

| Feature | Free Users | Premium Users |
|---|---|---|
| Active URLs | Max 10 | Unlimited |
| Custom Aliases | ❌ Not allowed | ✅ Allowed |
| Detailed Analytics | ❌ Not allowed | ✅ Full access |

### 3.3 Security Best Practices

- **Rate limiting** on login endpoint (e.g., 5 attempts per minute)
- **Secure password storage** using Django's built-in hashing
- **Sanitize all URL inputs** before processing

---

## 4. API Endpoint Specifications

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
| `GET` | `/{short_code}/` | Redirect (HTTP 302/301) — triggers Redis lookup + async analytics |

### Analytics *(Premium only)*

| Method | Endpoint | Description |
|---|---|---|
| `GET` | `/api/v1/analytics/{short_code}/` | Time-series + geo-location analytics |

---

## 5. Project Roadmap & Milestones

| Phase | Days | Module | Deliverables |
|---|---|---|---|
| Foundation | 1–3 | Module 5 | Docker setup, MVP endpoints, Swagger docs |
| Data Logic | 4–6 | Module 6 | Models, migrations, managers, ORM optimization |
| **Security** | **7–9** | **Module 7** | **JWT auth, custom permissions, RBAC, rate limiting** |
| Scale | 10–12 | Module 8 | Redis caching, Celery async tasks |
| Integration | 13–15 | Module 9 | URL preview service, QA, documentation |

---

## 6. Technical Stack

| Category | Technology |
|---|---|
| Language | Python 3.11+ |
| Framework | Django 5.0+ & DRF |
| Database | PostgreSQL 15+ |
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
