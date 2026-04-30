# Hospital Management System – Spring Data JPA

## Complexity

Advanced | Time Estimate: 10–12 hours

---

## Project Overview

This phase enhances the existing Hospital Management System by integrating **Spring Data JPA** and advanced persistence techniques. The focus is on repository abstraction, query optimization, transaction management, pagination, sorting, and caching.

Learners will implement derived queries, custom JPQL and native SQL queries, and apply transactional boundaries while improving system performance compared to the previous module.

---

## Project Objectives

By the end of this project, learners will be able to:

* Use Spring Data JPA to simplify database access via repository interfaces.
* Implement CRUD operations, pagination, and sorting.
* Manage transactions using @Transactional (propagation, isolation, rollback).
* Create custom JPQL and native SQL queries.
* Apply caching using Spring Cache to improve performance.
* Optimize searching, filtering, and retrieval logic.

---

## Epics and User Stories

### Epic 1: Spring Data Integration

**User Story 1.1**
As a developer, I want to integrate Spring Data JPA for consistent database access.

**Acceptance Criteria**

* Spring Data JPA dependency configured
* Entities annotated (@Entity, @Id, relationships)
* Repositories extend JpaRepository/CrudRepository
* Application connects to existing database

---

### Epic 2: Repository and Query Development

**User Story 2.1**
As an administrator, I want to manage hospital data using repositories.

**Acceptance Criteria**

* Repositories created for Patient, Doctor, Department, Appointment, Prescription, PrescriptionItem, PatientFeedback, MedicalInventory
* Derived query methods implemented
* Custom queries using @Query (JPQL and native SQL)

**User Story 2.2**
As a receptionist, I want to browse data using pagination and sorting.

**Acceptance Criteria**

* Pagination using Pageable
* APIs return paginated results
* Performance documented

---

### Epic 3: Transaction Management and Optimization

**User Story 3.1**
As a developer, I want transactional integrity for booking and prescriptions.

**Acceptance Criteria**

* @Transactional applied correctly
* Propagation and isolation levels demonstrated
* Rollback verified on failure scenarios

**User Story 3.2**
As an analyst, I want optimized queries for better performance.

**Acceptance Criteria**

* Complex JPQL queries optimized
* Index usage validated
* Query performance measured

---

### Epic 4: Caching and Performance Enhancement

**User Story 4.1**
As a receptionist, I want faster access to frequently used data.

**Acceptance Criteria**

* Spring Cache implemented (@EnableCaching)
* @Cacheable and @CacheEvict used appropriately
* Cache invalidation handled correctly
* Performance improvements measured

---

### Epic 5: Reporting and Documentation

**User Story 5.1**
As a contributor, I want clear documentation of repositories and optimizations.

**Acceptance Criteria**

* Repository and query logic documented
* Transaction strategies explained
* README updated with caching and setup instructions

---

## Technical Requirements

| Area            | Description                                               |
| --------------- | --------------------------------------------------------- |
| Framework       | Spring Boot 3.x (Spring Data JPA, Cache, Validation, AOP) |
| Language        | Java 21                                                   |
| Database        | MySQL / PostgreSQL                                        |
| Architecture    | Layered (Controller → Service → Repository)               |
| Repositories    | JpaRepository / CrudRepository                            |
| Transactions    | @Transactional with propagation and rollback              |
| Queries         | Derived, JPQL, native SQL                                 |
| Caching         | Spring Cache (@EnableCaching, @Cacheable, @CacheEvict)    |
| Testing         | Postman / GraphQL / JavaFX                                |
| DSA Integration | Sorting and pagination optimization                       |

---

## Deliverables

| Deliverable             | Description                                |
| ----------------------- | ------------------------------------------ |
| Spring Data Integration | CRUD, pagination, sorting via repositories |
| Custom Queries          | JPQL and native SQL queries                |
| Transaction Management  | Tested rollback scenarios                  |
| Caching Implementation  | Configured caching with eviction strategy  |
| Performance Report      | Before/after optimization comparison       |
| API Documentation       | Updated OpenAPI docs                       |
| README File             | Setup and usage guide                      |

---

## Evaluation Criteria

| Category                     | Description                 | Points |
| ---------------------------- | --------------------------- | ------ |
| Spring Data Integration      | CRUD, pagination, sorting   | 20     |
| Custom Queries               | JPQL and native SQL         | 20     |
| Transaction Management       | @Transactional usage        | 15     |
| Caching Implementation       | Effective caching strategy  | 15     |
| Performance Optimization     | Measurable improvements     | 15     |
| Documentation & Code Quality | Clean and maintainable code | 15     |

**Total: 100 Points**
