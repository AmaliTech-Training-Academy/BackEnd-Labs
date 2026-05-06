# Smart E-Commerce System

## Database Fundamentals

Complexity: Advanced  |  Time Estimate: 10–12 hours

## Project Objectives

By the end of this project, learners will be able to:

* Design and normalize a relational database schema that models an e-commerce domain effectively.
* Develop conceptual, logical, and physical database models to ensure scalability and maintainability.
* Implement CRUD operations and complex queries using SQL and JDBC.
* Apply indexing, hashing, searching, and sorting algorithms to optimize database access.
* Integrate database operations into a JavaFX application interface for practical interaction.
* Compare relational and NoSQL designs for unstructured data storage such as user reviews or logs.
* Measure and document performance improvement through optimization and indexing.

## Project Description

This stage of the Smart E-Commerce System focuses on building the data layer and persistence logic that will power the full application in later modules.

Students will design a relational database for an e-commerce system, implement the schema using SQL, and integrate it with a JavaFX application that performs essential operations — including product listing, searching, order management, and reporting.

The system must reflect real-world e-commerce logic (users, products, orders, reviews, inventory) while incorporating data structure and algorithm concepts (caching, indexing, sorting, searching) to enhance performance.

## Epics and User Stories

### Epic 1: Database Design and Modeling

**User Story 1.1:**
As a database designer, I want to create conceptual, logical, and physical database models so that the data structure is clear and efficient.

**Acceptance Criteria:**

* Conceptual ERD includes all major entities and relationships.
* Logical model defines attributes, primary keys, and foreign keys.
* Physical model includes SQL data types, constraints, and normalization (up to 3NF).

**User Story 1.2:**
As a database administrator, I want to define indexes and relationships so that queries run efficiently and data integrity is maintained.

**Acceptance Criteria:**

* Appropriate primary and foreign keys are applied.
* Indexes are defined on frequently searched or joined columns.
* Referential integrity and constraints are enforced.

### Epic 2: Data Access and CRUD Operations

**User Story 2.1:**
As an administrator, I want to add, update, and delete product and category data from the JavaFX interface so that I can manage inventory.

**Acceptance Criteria:**

* All CRUD operations functional via JavaFX interface.
* Input validation and feedback implemented.
* Constraints prevent duplicate or invalid entries.

**User Story 2.2:**
As a user, I want to view products and their details so that I can browse and make purchase decisions.

**Acceptance Criteria:**

* Product listings dynamically loaded from database.
* Pagination and search filters implemented.
* Parameterized JDBC queries used.

### Epic 3: Searching, Sorting, and Optimization

**User Story 3.1:**
As a customer, I want to search products quickly so I can find items efficiently.

**Acceptance Criteria:**

* Case-insensitive search implemented.
* Indexing or hashing used for optimization.
* Performance improvement documented.

**User Story 3.2:**
As a developer, I want caching and sorting so frequently accessed data loads faster.

**Acceptance Criteria:**

* In-memory caching implemented (Map/List).
* Sorting/searching algorithms applied.
* Cache invalidation ensures consistency.

### Epic 4: Performance and Optimization

**User Story 4.1:**
As an analyst, I want performance reports before and after optimization.

**Acceptance Criteria:**

* Query times recorded before/after indexing.
* Performance improvements clearly shown.

**User Story 4.2:**
As a developer, I want NoSQL support for reviews/logs.

**Acceptance Criteria:**

* NoSQL schema defined.
* Justification provided.

### Epic 5: Reporting and Documentation

**User Story 5.1:**
As a contributor, I want proper documentation.

**Acceptance Criteria:**

* ERDs included.
* SQL scripts provided.
* README included.

## Technical Requirements

### Database

* MySQL/PostgreSQL
* 3NF normalization
* Entities: Users, Products, Categories, Orders, OrderItems, Reviews, Inventory
* Indexing on frequently queried fields

### Application (JavaFX + JDBC)

* CRUD operations via UI
* Parameterized queries
* Layered architecture (Controller → Service → DAO)
* Caching using in-memory structures

### DSA Integration

* Hashing for fast lookup
* Sorting/searching algorithms
* Indexing concept mapping
* Performance measurement

## Evaluation Criteria

* Database Design: 25 pts
* SQL Implementation: 20 pts
* JavaFX + JDBC: 20 pts
* DSA Application: 15 pts
* Performance Optimization: 10 pts
* Documentation: 10 pts

Total: 100 pts
