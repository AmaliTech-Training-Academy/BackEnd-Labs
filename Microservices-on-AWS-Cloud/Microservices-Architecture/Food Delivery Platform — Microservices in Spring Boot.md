# Food Delivery Platform — Microservices in Spring Boot

**Complexity:** Advanced | **Time estimate:** 14–18 hours

---

## Project Overview

You are given a fully working monolithic food delivery backend. The monolith contains Customer Management, Restaurant and Menu Management, Order Management, and Delivery and Notification functionality — all in a single Spring Boot application sharing one database.

Your objective is to refactor this monolith into four independently deployable microservices, each with its own database, containerized with Docker, connected through Eureka service discovery and Spring Cloud Gateway, and communicating asynchronously via RabbitMQ.

---

## Starter Monolith: What You Receive

Review the GitHub repo carefully before starting.

**Monolith structure:**

| Package / Layer | Description |
|----------------|-------------|
| `model/` | Customer, Restaurant, MenuItem, Order, OrderItem, Delivery entities sharing one database |
| `repository/` | JPA repositories with cross-entity queries and joins across domains |
| `service/` | Business logic with direct method calls between domains (e.g., OrderService calls RestaurantRepository) |
| `controller/` | REST controllers exposing all endpoints from one application on port 8080 |
| `dto/` | Request and response DTOs for all operations |
| `exception/` | Global exception handling |
| `config/` | Security configuration with JWT authentication |
| `application.yml` | Single database connection, single port (8080) |

**Key problems to solve:**

- All entities share one PostgreSQL database with foreign key relationships across domains
- Services call each other via in-process method invocations (OrderService calls RestaurantRepository directly)
- Delivery status updates are sent synchronously inside the order flow, blocking the response
- The entire application is one JAR — scaling order processing means scaling everything
- A bug in one domain (e.g., delivery tracking) can crash the entire application

---

## Epics and User Stories

### Epic 1: Service Decomposition and Database Separation

**User story 1.1** — As a developer, I want to decompose the monolith into four microservices so that each service can be developed, deployed, and scaled independently.

Acceptance criteria:

- Four separate Spring Boot projects, each with its own `pom.xml` and application entry point
- Each service has its own database: `customer_db`, `restaurant_db`, `order_db`, `delivery_db`
- Foreign key relationships replaced with ID references and API calls
- Each service runs on its own port and starts independently

**User story 1.2** — As a developer, I want to replace direct entity relationships with REST-based communication so that services are loosely coupled and database-independent.

Acceptance criteria:

- Order Service calls Restaurant Service via REST to validate menu items and prices before placing an order
- Order Service calls Customer Service via REST to validate customer existence and delivery address
- Delivery Service calls Order Service via REST to fetch order details when assigning a delivery
- OpenFeign clients defined for all inter-service calls
- Graceful error handling when a dependent service is unavailable

---

### Epic 2: Containerization with Docker

**User story 2.1** — As a DevOps engineer, I want each microservice containerized with Docker so that the entire system can be started with a single command.

Acceptance criteria:

- Each microservice has a Dockerfile using multi-stage builds (build and runtime stages)
- A root `docker-compose.yml` defines all services, databases, and infrastructure
- `docker compose up` starts the complete system (4 services + PostgreSQL + RabbitMQ + Eureka + Gateway)
- Health checks configured; services start in correct dependency order

**User story 2.2** — As a developer, I want Docker-specific Spring profiles so that services use container hostnames and environment variables for configuration.

Acceptance criteria:

- `application-docker.yml` profiles created for each service with container-aware settings
- Database URLs use Docker service names (e.g., `jdbc:postgresql://postgres:5432/customer_db`)
- Sensitive values passed via environment variables, not hardcoded
- `.dockerignore` files exclude unnecessary build artifacts

---

### Epic 3: Service Discovery and API Gateway

**User story 3.1** — As a developer, I want to implement service discovery with Eureka so that services can find each other dynamically without hardcoded URLs.

Acceptance criteria:

- Eureka Server created as a standalone Spring Boot service
- All four microservices register with Eureka on startup
- Eureka dashboard accessible at `http://localhost:8761` showing all registered services
- Services use logical names (e.g., `http://customer-service`) instead of IP and port

**User story 3.2** — As a developer, I want an API Gateway so that external clients access all services through a single entry point with centralized routing, authentication, and rate limiting.

Acceptance criteria:

- Spring Cloud Gateway routes requests:
  - `/api/customers/` → Customer Service
  - `/api/restaurants/` → Restaurant Service
  - `/api/orders/` → Order Service
  - `/api/deliveries/` → Delivery Service
- JWT authentication filter validates tokens at the gateway level
- Gateway integrates with Eureka for load-balanced routing (e.g., `lb://customer-service`)
- Rate limiting configured on high-traffic endpoints (e.g., order placement)

---

### Epic 4: Event-Driven Communication

**User story 4.1** — As a developer, I want to replace synchronous delivery and notification calls with event-driven messaging so that the order placement flow is not blocked by downstream processing.

Acceptance criteria:

- RabbitMQ integrated as the message broker
- Order Service publishes `OrderPlacedEvent` and `OrderCancelledEvent` to a topic exchange
- Delivery Service consumes `OrderPlacedEvent` to create delivery assignments automatically
- Delivery Service publishes `DeliveryStatusUpdatedEvent` when a driver picks up or delivers an order
- Dead letter queue configured for failed message processing

**User story 4.2** — As a developer, I want to implement circuit breakers on inter-service calls so that one service being down does not cascade failures to the entire system.

Acceptance criteria:

- Resilience4j circuit breakers configured on all Feign clients
- Fallback responses defined for each inter-service call (e.g., if Restaurant Service is down, Order Service returns a clear error rather than timing out)
- Circuit breaker states (`CLOSED`, `OPEN`, `HALF-OPEN`) observable via Actuator endpoints
- System remains functional even when Delivery Service is down (orders can still be placed)

---

### Epic 5: Testing and Documentation

**User story 5.1** — As a QA engineer, I want to test the microservices system end-to-end so that all features work correctly after the migration.

Acceptance criteria:

- Postman collection provided testing all API endpoints through the gateway
- Full order flow verified: register customer → browse restaurants → place order → delivery assigned → delivery completed
- Event-driven delivery assignment verified: place order → delivery record appears automatically
- Fault tolerance verified: stop one service → others continue working

**User story 5.2** — As a reviewer, I want comprehensive documentation so that the migration decisions and architecture are clearly explained.

Acceptance criteria:

- Architecture diagram showing all services, databases, gateway, and message flows
- API contract documentation for each service (endpoints, request and response formats)
- Migration decision log explaining why each boundary was chosen
- README with setup instructions for running the entire system

---

## Target Architecture

```
Client (Browser / Postman)
        │
        ▼
API Gateway (:8080)  ──  JWT auth filter  ──  Rate limiter
    │
    ├── /api/customers/**    →  Customer Service (:8081)    →  customer_db
    ├── /api/restaurants/**  →  Restaurant Service (:8082)  →  restaurant_db
    ├── /api/orders/**       →  Order Service (:8083)       →  order_db
    └── /api/deliveries/**   →  Delivery Service (:8084)    →  delivery_db

Eureka Server (:8761)  ──  Service registry
RabbitMQ (:5672)       ──  Event bus
                              OrderPlacedEvent
                              OrderCancelledEvent
                              DeliveryStatusUpdatedEvent
```

---

## Technical Requirements

| Area | Description |
|------|-------------|
| **Framework** | Spring Boot 3.x (Web, JPA, Security, Cloud) |
| **Language** | Java 21 |
| **Containerization** | Docker with multi-stage Dockerfiles; Docker Compose for orchestration |
| **Service discovery** | Spring Cloud Netflix Eureka |
| **API gateway** | Spring Cloud Gateway with route predicates and filters |
| **Inter-service communication** | OpenFeign for REST calls; RabbitMQ for async events |
| **Fault tolerance** | Resilience4j circuit breakers with fallback handlers |
| **Database** | PostgreSQL (separate DB per service) |
| **Authentication** | JWT-based auth at the API Gateway level |
| **Testing** | Postman collections for end-to-end API testing |
| **Documentation** | Architecture diagrams, API contracts, migration decision log, README |

---

## Deliverables

| Deliverable | Description |
|-------------|-------------|
| **Decomposed microservices** | Four independent Spring Boot services with separate databases and clean API boundaries |
| **Docker setup** | Dockerfiles for each service and a `docker-compose.yml` that starts the full system |
| **Service discovery and gateway** | Eureka Server and Spring Cloud Gateway with routing, auth filter, and rate limiting |
| **Event-driven messaging** | RabbitMQ integration with event publishing, consuming, and dead letter queue |
| **Fault tolerance** | Circuit breakers on inter-service calls with fallback responses |
| **API test collection** | Postman collection testing all endpoints through the gateway |
| **Documentation** | Architecture diagram, API contracts, migration log, and setup README |

---

## Evaluation Criteria

| Category | Description | Points |
|----------|-------------|--------|
| **Service decomposition** | Clean separation of domains, independent databases, proper API boundaries | 20 |
| **Containerization** | Multi-stage Dockerfiles, Docker Compose orchestration, health checks, correct startup order | 15 |
| **Service discovery and gateway** | Eureka registration, gateway routing, JWT auth filter, rate limiting | 20 |
| **Event-driven communication** | RabbitMQ events, async delivery flow, dead letter queue handling | 15 |
| **Fault tolerance** | Circuit breakers, fallback responses, graceful degradation when services are down | 10 |
| **Code quality and documentation** | Clean code, architecture diagrams, API contracts, migration log, clear README | 20 |
| **Total** | | **100 pts** |
