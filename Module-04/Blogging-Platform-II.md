# Blogging Platform 

---

## Project Objectives

By the end of this project, learners will be able to:

* Design and normalize a relational or non-relational database schema that models a blogging domain effectively.
* Develop conceptual, logical, and physical database models to ensure scalability and maintainability.
* Implement CRUD operations and complex queries using SQL (or equivalent NoSQL queries) and JDBC.
* Apply indexing, caching, searching, and sorting algorithms to optimize database access and performance.
* Integrate database operations into a JavaFX application interface for interactive content management.
* Compare relational (SQL) and NoSQL designs for unstructured data storage such as comments or reviews.
* Measure and document performance improvement through optimization and indexing techniques.

---

## Project Overview

This stage of the Smart Blogging Platform focuses on building the data layer and persistence logic that will support all future modules.

Students will design a relational or non-relational database for a blogging system, implement the schema using SQL or NoSQL, and integrate it with a JavaFX application that performs core operations, including post creation, comment management, tag assignment, and analytics reporting.

The system must reflect real-world blogging logic (users, posts, comments, tags, and reviews) while incorporating Data Structures and Algorithms (DSA) concepts such as indexing, caching, sorting, and searching to enhance performance and scalability.

---

## Epics and User Stories

### Epic 1: Database Design and Modeling

**User Story 1.1**

As a database designer, I want to create conceptual, logical, and physical database models so that the data structure of the blogging platform is efficient and scalable.

**Acceptance Criteria:**

* Conceptual ERD or NoSQL schema includes all major entities and relationships.
* Logical model defines attributes, primary/foreign keys, and relationships.
* Physical model includes SQL data types, constraints, and normalization (up to 3NF where applicable).

**User Story 1.2**

As a database administrator, I want to define indexes and relationships so that queries and lookups run efficiently while maintaining data integrity.

**Acceptance Criteria:**

* Appropriate primary and foreign keys defined.
* Indexes created on frequently queried columns (post title, author ID, tag name).
* Referential integrity enforced.

---

### Epic 2: Data Access and CRUD Operations

**User Story 2.1**

As a blogger, I want to add, update, and delete blog posts and comments through a JavaFX interface so that I can manage my content easily.

**Acceptance Criteria:**

* All CRUD operations functional via JavaFX interface.
* Input validation and user feedback implemented.
* Database constraints prevent duplicates or invalid entries.

**User Story 2.2**

As a reader, I want to view and search for blog posts and their details so that I can explore content of interest.

**Acceptance Criteria:**

* Post listings dynamically retrieved from database.
* Pagination, filters, and search functions implemented.
* Parameterized queries used via JDBC or NoSQL driver.

---

### Epic 3: Searching, Sorting, and Optimization

**User Story 3.1**

As a reader, I want to search for posts quickly by keyword, tag, or author so that I can find relevant articles efficiently.

**Acceptance Criteria:**

* Case-insensitive search implemented.
* Indexing or hashing improves search performance.
* Performance improvements documented.

**User Story 3.2**

As a developer, I want to implement caching and sorting so frequently accessed posts are retrieved faster.

**Acceptance Criteria:**

* In-memory caching using Maps or Lists.
* Sorting/search algorithms applied.
* Cache invalidation ensures consistency.

---

### Epic 4: Performance and Query Optimization

**User Story 4.1**

As an analyst, I want performance reports comparing pre- and post-optimization queries.

**Acceptance Criteria:**

* Query execution times recorded before/after optimization.
* Indexing and caching demonstrate measurable gains.

**User Story 4.2**

As a developer, I want to store comments/reviews in NoSQL format for flexibility.

**Acceptance Criteria:**

* NoSQL schema defined for unstructured data.
* Justification provided.
* Optional SQL vs NoSQL comparison included.

---

### Epic 5: Reporting and Documentation

**User Story 5.1**

As a contributor, I want full documentation for maintainability.

**Acceptance Criteria:**

* ERDs or schema diagrams included.
* SQL/NoSQL scripts provided.
* README with setup instructions.

---

## Technical Requirements

### Database

* MySQL / PostgreSQL or MongoDB
* Normalized to 3NF (SQL)
* Entities: Users, Posts, Comments, Tags, Reviews
* Indexes on frequently queried fields
* Referential integrity enforced

### Application Layer (JavaFX + JDBC/NoSQL)

* JavaFX UI for CRUD, search, analytics
* JDBC or MongoDB driver with parameterized queries
* Layered architecture (Controller → Service → DAO)
* In-memory caching (Maps, Lists)

### Data Structures & Algorithms

* Hashing for fast lookup
* Sorting and searching algorithms
* Indexing concept mapping
* Performance measurement before/after optimization

---

## Deliverables

* Database Design Document
* SQL / NoSQL Implementation Script
* JavaFX Application
* Performance Report
* README File
* Testing Evidence

---

## Evaluation Criteria

* Database Design: 25 pts
* SQL / NoSQL Implementation: 20 pts
* JavaFX + JDBC Integration: 20 pts
* DSA Application: 15 pts
* Performance Optimization: 10 pts
* Documentation & Code Quality: 10 pts

**Total: 100 pts**
