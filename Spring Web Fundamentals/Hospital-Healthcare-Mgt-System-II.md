# Hospital / Healthcare Management System

## Complexity

Advanced | Time Estimate: 10–12 hours

---

## Project Overview

This phase transforms the Hospital Management System into a **Spring Boot web application**. It focuses on building **RESTful and GraphQL APIs** that interact with the underlying database while applying enterprise-level backend concepts such as validation, exception handling, AOP, and OpenAPI documentation.

The system models real-world hospital operations including **patients, doctors, departments, and appointments**, ensuring scalability, maintainability, and clean architecture.

---

## Project Objectives

By the end of this project, learners will be able to:

* Apply Spring Boot configuration principles, IoC, and Dependency Injection for modular applications.
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
As an administrator, I want to manage patients, doctors, and departments through REST endpoints.

**Acceptance Criteria**

* CRUD APIs implemented following REST conventions
* Responses structured with status, message, and data
* Controller → Service → Repository architecture applied

**User Story 2.2**
As a receptionist, I want to view, sort, and filter patients and appointments.

**Acceptance Criteria**

* Pagination, sorting, and filtering supported
* Efficient retrieval algorithms applied
* Performance documented and analyzed

---

### Epic 3: Validation, Exception Handling, and Documentation

**User Story 3.1**
As a developer, I want to validate and document APIs.

**Acceptance Criteria**

* Bean Validation applied to DTOs
* Custom validation rules implemented
* OpenAPI/Swagger documentation generated automatically

---

### Epic 4: GraphQL Integration

**User Story 4.1**
As a frontend developer, I want to fetch data using GraphQL queries and mutations.

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
* AOP behavior documented

---

## Technical Requirements

| Area                   | Description                                              |
| ---------------------- | -------------------------------------------------------- |
| Framework              | Spring Boot 3.x (Web, Validation, AOP, GraphQL, OpenAPI) |
| Language               | Java 21                                                  |
| Database               | Relational database from Module 1                        |
| Architecture           | Layered (Controller → Service → Repository)              |
| Validation             | Bean Validation + custom validators                      |
| Documentation          | Springdoc OpenAPI (Swagger)                              |
| Cross-Cutting Concerns | Logging and monitoring via AOP                           |
| Testing                | Postman / JavaFX / web frontend                          |
| DSA Integration        | Sorting, searching, pagination algorithms                |

---

## Deliverables

| Deliverable                     | Description                                  |
| ------------------------------- | -------------------------------------------- |
| Spring Boot Web Application     | REST + GraphQL backend connected to database |
| Validation & Exception Handling | DTO validation and global error handling     |
| API Documentation               | Swagger/OpenAPI documentation                |
| AOP Implementation              | Logging and monitoring aspects               |
| GraphQL Schema                  | Queries and mutations defined                |
| Performance Report              | REST vs GraphQL analysis                     |
| README File                     | Setup and API usage guide                    |

---

## Evaluation Criteria

| Category                        | Description                           | Points |
| ------------------------------- | ------------------------------------- | ------ |
| Spring Boot Configuration & IoC | Proper setup and dependency injection | 15     |
| REST API Development            | CRUD and REST architecture            | 20     |
| Validation & Documentation      | Validation, error handling, OpenAPI   | 20     |
| GraphQL Integration             | Schema, queries, mutations            | 15     |
| AOP & Optimization              | Logging and monitoring                | 15     |
| Code Quality & Reporting        | Clean code and documentation          | 15     |

**Total: 100 Points**
