# Smart E-Commerce System

---

## Project Overview
### Advanced | Time Estimate: 10–12 hours

This phase transforms the Smart E-Commerce System into a full **Spring Boot web application**, focusing on building **RESTful and GraphQL APIs**. The system applies enterprise-level backend concepts including validation, exception handling, AOP, and API documentation.

The goal is to evolve the existing database foundation into a scalable, modular, and well-documented backend system using Spring Boot.

---

## Project Objectives

By the end of this project, learners will be able to:

* Apply Spring Boot configuration principles, IoC, and Dependency Injection to build modular applications.
* Develop RESTful APIs using layered architecture (Controller → Service → Repository).
* Implement validation, exception handling, and API documentation using Bean Validation, @ControllerAdvice, and Springdoc OpenAPI.
* Integrate GraphQL schemas, queries, and mutations for flexible data retrieval.
* Apply AOP and algorithmic techniques for logging, monitoring, sorting, searching, and pagination.

---

## Epics and User Stories

### Epic 1: Application Setup and Dependency Management

**User Story 1.1**
As a developer, I want to configure and structure a Spring Boot project so that it runs efficiently across multiple environments.

**Acceptance Criteria**

* Spring Boot project initialized with required dependencies
* Profiles configured for dev, test, and prod
* Constructor-based dependency injection used consistently

---

### Epic 2: RESTful API Development

**User Story 2.1**
As an administrator, I want to manage users, products, and categories through REST endpoints.

**Acceptance Criteria**

* CRUD APIs implemented following REST standards
* Standard response structure: status, message, data
* Controller → Service → Repository architecture applied

**User Story 2.2**
As a customer, I want to view, sort, and filter products.

**Acceptance Criteria**

* Pagination, sorting, and filtering supported
* Efficient retrieval logic implemented
* Performance documented

---

### Epic 3: Validation, Exception Handling, and Documentation

**User Story 3.1**
As a developer, I want to validate and document APIs.

**Acceptance Criteria**

* Bean Validation applied to DTOs
* Custom validation rules implemented where necessary
* OpenAPI/Swagger documentation generated

---

### Epic 4: GraphQL Integration

**User Story 4.1**
As a frontend developer, I want to use GraphQL to retrieve only required data.

**Acceptance Criteria**

* GraphQL schema defined for core entities
* Queries and mutations implemented
* REST and GraphQL coexist without conflict

---

### Epic 5: Cross-Cutting Concerns (AOP)

**User Story 5.1**
As a developer, I want centralized logging and monitoring using AOP.

**Acceptance Criteria**

* @Before, @After, @Around aspects implemented
* Logging applied to service layer methods
* AOP usage documented

---

## Technical Requirements

| Area                   | Description                                              |
| ---------------------- | -------------------------------------------------------- |
| Framework              | Spring Boot 3.x (Web, Validation, AOP, GraphQL, OpenAPI) |
| Language               | Java 21                                                  |
| Database               | Relational database from previous module                 |
| Architecture           | Layered (Controller → Service → Repository)              |
| Validation             | Bean Validation + custom validators                      |
| Documentation          | Springdoc OpenAPI (Swagger)                              |
| Cross-Cutting Concerns | Logging and monitoring via AOP                           |
| Testing                | Postman / frontend / JavaFX integration                  |
| DSA Integration        | Sorting, searching, pagination algorithms                |

---

## Deliverables

| Deliverable                     | Description                                  |
| ------------------------------- | -------------------------------------------- |
| Spring Boot Application         | REST + GraphQL backend connected to database |
| Validation & Exception Handling | DTO validation and global error handling     |
| API Documentation               | Swagger/OpenAPI documentation                |
| AOP Implementation              | Logging and monitoring aspects               |
| GraphQL Schema                  | Queries and mutations defined                |
| Performance Report              | REST vs GraphQL comparison                   |
| README File                     | Setup and API usage guide                    |

---

## Evaluation Criteria

| Category                        | Description                           | Points |
| ------------------------------- | ------------------------------------- | ------ |
| Spring Boot Configuration & IoC | Proper setup and dependency injection | 15     |
| REST API Development            | Functional CRUD and REST design       | 20     |
| Validation & Documentation      | Validation, error handling, OpenAPI   | 20     |
| GraphQL Integration             | Schema, queries, and mutations        | 15     |
| AOP & Optimization              | Logging and performance monitoring    | 15     |
| Code Quality & Reporting        | Clean code and documentation          | 15     |

**Total: 100 Points**
