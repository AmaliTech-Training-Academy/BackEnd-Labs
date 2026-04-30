
# Hospital/Healthcare Management System

---

### Project Objectives

By the end of this project, learners will be able to:

- Design and normalize a relational database schema that models a hospital management domain effectively
- Develop conceptual, logical, and physical database models to ensure scalability and maintainability
- Implement CRUD operations and complex queries using SQL and JDBC
- Apply indexing, hashing, searching, and sorting algorithms to optimize database access
- Integrate database operations into a JavaFX application interface for practical interaction
- Compare relational and NoSQL designs for unstructured data storage such as patient notes or medical logs
- Measure and document performance improvement through optimization and indexing

---

### Project Overview

This stage of the Hospital Management System focuses on building the data layer and persistence logic that will power the full application in later modules. Students will design a relational database for a hospital management system, implement the schema using SQL, and integrate it with a JavaFX application that performs essential operations — including patient registration, appointment scheduling, medical records management, and reporting.

The system must reflect real-world hospital logic (patients, doctors, departments, appointments, prescriptions, medical inventory) while incorporating data structure and algorithm concepts (caching, indexing, sorting, searching) to enhance performance.

---

### Epics and User Stories

#### Epic 1: Database Design and Modeling

**User Story 1.1**

> As a database designer, I want to create conceptual, logical, and physical database models so that the data structure is clear and efficient.

**Acceptance Criteria:**
- Conceptual ERD includes all major entities and relationships
- Logical model defines attributes, primary keys, and foreign keys
- Physical model includes SQL data types, constraints, and normalization (up to 3NF)

**User Story 1.2**

> As a database administrator, I want to define indexes and relationships so that queries run efficiently and data integrity is maintained.

**Acceptance Criteria:**
- Appropriate primary and foreign keys are applied
- Indexes are defined on frequently searched or joined columns
- Referential integrity and constraints are enforced

---

#### Epic 2: Data Access and CRUD Operations

**User Story 2.1**

> As an administrator, I want to add, update, and delete patient and doctor data from the JavaFX interface so that I can manage hospital records.

**Acceptance Criteria:**
- All CRUD operations are functional via the JavaFX interface
- Input validation and feedback messages are implemented
- Database constraints prevent duplicate or invalid entries

**User Story 2.2**

> As a receptionist, I want to view patients and their medical history from the application so that I can assist with registration and appointment scheduling.

**Acceptance Criteria:**
- Patient listings are displayed dynamically from the database
- Pagination or search filters improve usability
- Data is retrieved using parameterized queries through JDBC

---

#### Epic 3: Searching, Sorting, and Optimization

**User Story 3.1**

> As a receptionist, I want to search for patients quickly by name or ID so that I can locate records efficiently.

**Acceptance Criteria:**
- Patient search is case-insensitive and responsive
- Search optimization is achieved through indexing and/or hashing
- Measurable improvement in query response time is documented

**User Story 3.2**

> As a developer, I want to implement in-memory caching and sorting so that frequently accessed or sorted data is retrieved faster.

**Acceptance Criteria:**
- Caching layer implemented using in-memory structures (e.g., maps or lists)
- Sorting and searching algorithms integrated and documented
- Cache invalidation logic ensures data consistency after updates

---

#### Epic 4: Performance and Query Optimization

**User Story 4.1**

> As an analyst, I want to generate performance reports comparing pre- and post-optimization so that I can measure system efficiency.

**Acceptance Criteria:**
- Query execution times recorded before and after optimization
- Indexes and caching demonstrate measurable performance gains
- Report clearly communicates methodology and findings

**User Story 4.2**

> As a developer, I want to explore storing patient notes or medical logs in a NoSQL format so that unstructured data can be efficiently handled.

**Acceptance Criteria:**
- NoSQL data model created for patient notes or medical logs
- Justification provided for why NoSQL is suitable for the use case
- Optional implementation comparison included in performance report

---

#### Epic 5: Reporting and Documentation

**User Story 5.1**

> As a project contributor, I want to produce documentation and reports so that the project can be reviewed, reused, or extended.

**Acceptance Criteria:**
- ERD diagrams and database documentation included
- SQL scripts and sample data provided
- A README file describes setup, dependencies, and execution steps

---

### Technical Requirements

#### Database
- Use **MySQL** or **PostgreSQL** for the relational database implementation
- Database schema normalized to **Third Normal Form (3NF)**
- Include at least the following entity groups: `Patients`, `Doctors`, `Departments`, `Appointments`, `Prescriptions`, `PrescriptionItems`, `PatientFeedback`, `MedicalInventory`
- Define indexes on high-frequency columns (e.g., patient name, doctor ID, appointment date, department ID)
- Implement foreign keys to maintain referential integrity

#### Application Layer (JavaFX + JDBC)
- Use **JavaFX** for user interaction: patient registration, appointment scheduling, CRUD operations, and reporting
- Database access implemented using **JDBC** with parameterized queries to prevent SQL injection
- Logical separation of concerns: `Controller → Service → DAO`
- In-memory structures (e.g., `Map`, `List`) used to cache and sort results
- Include an admin panel for patient/doctor management and performance monitoring

#### Data Structures & Algorithms Integration
- **Hashing / Caching:** Use in-memory data structures to speed up lookups
- **Sorting & Searching:** Apply appropriate algorithms for ordering and filtering data
- **Indexing Concept:** Explain how in-memory structures mirror database index logic
- **Performance Measurement:** Demonstrate efficiency improvements from optimization efforts

---

### Deliverables

| Deliverable | Description |
|---|---|
| Database Design Document | Conceptual, logical, and physical models with ERDs and explanations |
| SQL Implementation Script | Scripts for creating tables, constraints, indexes, and inserting sample data |
| JavaFX Application | Functional interface that performs CRUD, search, and reporting using JDBC |
| Performance Report | Comparative analysis showing before/after optimization metrics (indexing, caching) |
| NoSQL Design *(Optional)* | Documented schema or implementation for storing unstructured data (e.g., patient notes) |
| README File | Setup guide, dependencies, how to run SQL scripts, and usage instructions |
| Testing Evidence | Screenshots or reports showing correct query results and validation outcomes |

---

### Evaluation Criteria

| Category | Evaluation Criteria | Points |
|---|---|---|
| Database Design | Conceptual, logical, and physical models are complete, normalized (3NF), and well-documented with ERDs | 25 |
| SQL Implementation | SQL schema is syntactically correct, includes constraints, sample data, indexes, and supports complex queries | 20 |
| JavaFX + JDBC Integration | Functional CRUD operations, UI usability, safe JDBC handling, and error feedback are correctly implemented | 20 |
| DSA Application | Clear use of caching, sorting, and searching with performance justification and accurate mapping to indexing concepts | 15 |
| Performance Optimization | Performance gains demonstrated through timing, analysis, and documentation | 10 |
| Documentation & Code Quality | README completeness, code organization, comments, and adherence to clean coding practices | 10 |
| **Total** | | **100 pts** |

---
---

## Module 4.2: Blogging Platform

**Complexity:** Advanced
**Time Estimate:** 10–12 hours

---

### Project Objectives

By the end of this project, learners will be able to:

- Design and normalize a relational or non-relational database schema that models a blogging domain effectively
- Develop conceptual, logical, and physical database models to ensure scalability and maintainability
- Implement CRUD operations and complex queries using SQL (or equivalent NoSQL queries) and JDBC
- Apply indexing, caching, searching, and sorting algorithms to optimize database access and performance
- Integrate database operations into a JavaFX application interface for interactive content management
- Compare relational (SQL) and NoSQL designs for unstructured data storage such as comments or reviews
- Measure and document performance improvement through optimization and indexing techniques

---

### Project Description

This stage of the Smart Blogging Platform focuses on building the data layer and persistence logic that will support all future modules. Students will design a relational or non-relational database for a blogging system, implement the schema using SQL or NoSQL, and integrate it with a JavaFX application that performs core operations — including post creation, comment management, tag assignment, and analytics reporting.

The system must reflect real-world blogging logic (users, posts, comments, tags, and reviews) while incorporating data structure and algorithm (DSA) concepts such as indexing, caching, sorting, and searching to enhance performance and scalability.

---

### Epics and User Stories

#### Epic 1: Database Design and Modeling

**User Story 1.1**

> As a database designer, I want to create conceptual, logical, and physical database models so that the data structure of the blogging platform is efficient and scalable.

**Acceptance Criteria:**
- Conceptual ERD or NoSQL schema includes all major entities and relationships
- Logical model defines attributes, primary/foreign keys, and relationships
- Physical model includes SQL data types, constraints, and normalization (up to 3NF where applicable)

**User Story 1.2**

> As a database administrator, I want to define indexes and relationships so that queries and lookups run efficiently while maintaining data integrity.

**Acceptance Criteria:**
- Appropriate primary and foreign keys (or references for NoSQL) are defined
- Indexes are created on frequently queried columns or document fields (e.g., post title, author ID, tag name)
- Referential integrity and constraints are enforced

---

#### Epic 2: Data Access and CRUD Operations

**User Story 2.1**

> As a blogger, I want to add, update, and delete blog posts and comments through a JavaFX interface so that I can manage my content easily.

**Acceptance Criteria:**
- All CRUD operations functional through the JavaFX interface
- Input validation and user feedback messages implemented
- Database constraints or schema validation prevent duplicate or invalid entries

**User Story 2.2**

> As a reader, I want to view and search for blog posts and their details so that I can explore content of interest.

**Acceptance Criteria:**
- Post listings displayed dynamically from the database
- Pagination, filters, or search functions implemented for improved usability
- Data retrieved using secure parameterized queries through JDBC or NoSQL driver

---

#### Epic 3: Searching, Sorting, and Optimization

**User Story 3.1**

> As a reader, I want to search for posts quickly by keyword, tag, or author so that I can find relevant articles efficiently.

**Acceptance Criteria:**
- Post search is case-insensitive and responsive
- Search performance improved through indexing or hashing
- Measurable improvement in query execution time documented

**User Story 3.2**

> As a developer, I want to implement caching and sorting so that frequently accessed posts are retrieved faster.

**Acceptance Criteria:**
- Caching layer implemented using in-memory data structures (e.g., Maps or Lists)
- Sorting and searching algorithms applied to cached data
- Cache invalidation ensures consistent results after updates

---

#### Epic 4: Performance and Query Optimization

**User Story 4.1**

> As an analyst, I want to generate performance reports comparing pre- and post-optimization queries so that I can measure system efficiency.

**Acceptance Criteria:**
- Query execution times recorded before and after applying indexes or caching
- Indexes and query optimizations demonstrate measurable performance gains
- Performance report clearly explains methodology and findings

**User Story 4.2**

> As a developer, I want to store user comments or reviews in a NoSQL format so that unstructured feedback can be handled flexibly.

**Acceptance Criteria:**
- NoSQL data model created for reviews or user comments
- Justification for using NoSQL documented (e.g., scalability, flexibility)
- Optional implementation comparison included in performance report

---

#### Epic 5: Reporting and Documentation

**User Story 5.1**

> As a project contributor, I want to document the database schema and project steps so that the system can be extended or maintained easily.

**Acceptance Criteria:**
- ERD diagrams or NoSQL schemas documented clearly
- SQL/NoSQL scripts and test data provided
- README file explains setup, dependencies, and execution instructions

---

### Technical Requirements

#### Database
- Use **MySQL** or **PostgreSQL** for the relational implementation, or **MongoDB** for NoSQL
- Schema normalized to **Third Normal Form (3NF)** for SQL databases
- Include at least these entity groups: `Users`, `Posts`, `Comments`, `Tags`, `Reviews`
- Define indexes on frequently queried columns (e.g., post title, tag name, author ID)
- Enforce referential integrity with foreign keys or document references

#### Application Layer (JavaFX + JDBC / NoSQL Driver)
- Use **JavaFX** for user interaction: displaying posts, searching, CRUD operations, and viewing analytics
- Database access implemented using **JDBC** (SQL) or **MongoDB Java Driver** (NoSQL) with parameterized queries to prevent injection
- Apply layered design: `Controller → Service → DAO`
- Use in-memory data structures (e.g., Maps, Lists) for caching and local sorting
- Include a dashboard for managing posts, viewing performance metrics, and performing optimizations

#### Data Structures & Algorithms Integration
- **Hashing / Caching:** Use in-memory structures to store frequently accessed posts and comments
- **Sorting & Searching:** Apply algorithms (e.g., QuickSort, Binary Search) to optimize query results
- **Indexing Concept:** Explain how database indexing relates to in-memory search and sorting
- **Performance Measurement:** Compare query response times before and after optimization

---

### Deliverables

| Deliverable | Description |
|---|---|
| Database Design Document | Conceptual, logical, and physical models with ERDs or NoSQL schema diagrams and explanations |
| SQL / NoSQL Implementation Script | Scripts for creating tables/collections, constraints, indexes, and inserting sample data |
| JavaFX Application | Interactive interface performing CRUD, search, and reporting functions using JDBC or NoSQL driver |
| Performance Report | Comparative analysis showing pre- and post-optimization metrics (indexing, caching, and query optimization) |
| NoSQL Design *(Optional)* | Documented schema or partial implementation for storing unstructured data such as comments or logs |
| README File | Setup guide including environment configuration, dependencies, database connection setup, and execution steps |
| Testing Evidence | Screenshots or console logs showing correct query results and validation outputs |

---

### Evaluation Criteria

| Category | Evaluation Criteria | Points |
|---|---|---|
| Database Design | Conceptual, logical, and physical models are complete, normalized (3NF), and well-documented with ERDs or schema diagrams | 25 |
| SQL / NoSQL Implementation | Schema or collections are syntactically correct, include constraints, indexes, and support complex queries | 20 |
| JavaFX + JDBC Integration | CRUD functionality, UI usability, and safe JDBC/driver handling correctly implemented with clear separation of concerns | 20 |
| DSA Application | Caching, sorting, and searching techniques applied with performance justification and accurate mapping to indexing concepts | 15 |
| Performance Optimization | Measurable improvements demonstrated through indexing, caching, and documented analysis | 10 |
| Documentation & Code Quality | README completeness, logical organization, code clarity, and adherence to clean coding standards | 10 |
| **Total** | | **100 pts** |

---
---

## Module 4.3: Smart E-Commerce System

**Complexity:** Advanced
**Time Estimate:** 10–12 hours

---

### Project Objectives

By the end of this project, learners will be able to:

- Design and normalize a relational database schema that models an e-commerce domain effectively
- Develop conceptual, logical, and physical database models to ensure scalability and maintainability
- Implement CRUD operations and complex queries using SQL and JDBC
- Apply indexing, hashing, searching, and sorting algorithms to optimize database access
- Integrate database operations into a JavaFX application interface for practical interaction
- Compare relational and NoSQL designs for unstructured data storage such as user reviews or logs
- Measure and document performance improvement through optimization and indexing

---

### Project Description

This stage of the Smart E-Commerce System focuses on building the data layer and persistence logic that will power the full application in later modules. Students will design a relational database for an e-commerce system, implement the schema using SQL, and integrate it with a JavaFX application that performs essential operations — including product listing, searching, order management, and reporting.

The system must reflect real-world e-commerce logic (users, products, orders, reviews, inventory) while incorporating data structure and algorithm concepts (caching, indexing, sorting, searching) to enhance performance.

---

### Epics and User Stories

#### Epic 1: Database Design and Modeling

**User Story 1.1**

> As a database designer, I want to create conceptual, logical, and physical database models so that the data structure is clear and efficient.

**Acceptance Criteria:**
- Conceptual ERD includes all major entities and relationships
- Logical model defines attributes, primary keys, and foreign keys
- Physical model includes SQL data types, constraints, and normalization (up to 3NF)

**User Story 1.2**

> As a database administrator, I want to define indexes and relationships so that queries run efficiently and data integrity is maintained.

**Acceptance Criteria:**
- Appropriate primary and foreign keys are applied
- Indexes are defined on frequently searched or joined columns
- Referential integrity and constraints are enforced

---

#### Epic 2: Data Access and CRUD Operations

**User Story 2.1**

> As an administrator, I want to add, update, and delete product and category data from the JavaFX interface so that I can manage inventory.

**Acceptance Criteria:**
- All CRUD operations are functional via the JavaFX interface
- Input validation and feedback messages are implemented
- Database constraints prevent duplicate or invalid entries

**User Story 2.2**

> As a user, I want to view products and their details from the application so that I can browse and make purchase decisions.

**Acceptance Criteria:**
- Product listings are displayed dynamically from the database
- Pagination or search filters improve usability
- Data is retrieved using parameterized queries through JDBC

---

#### Epic 3: Searching, Sorting, and Optimization

**User Story 3.1**

> As a customer, I want to search for products quickly by name or category so that I can find items efficiently.

**Acceptance Criteria:**
- Product search is case-insensitive and responsive
- Search optimization is achieved through indexing and/or hashing
- Measurable improvement in query response time is documented

**User Story 3.2**

> As a developer, I want to implement in-memory caching and sorting so that frequently accessed or sorted data is retrieved faster.

**Acceptance Criteria:**
- Caching layer implemented using in-memory structures (e.g., maps or lists)
- Sorting and searching algorithms integrated and documented
- Cache invalidation logic ensures data consistency after updates

---

#### Epic 4: Performance and Query Optimization

**User Story 4.1**

> As an analyst, I want to generate performance reports comparing pre- and post-optimization so that I can measure system efficiency.

**Acceptance Criteria:**
- Query execution times recorded before and after optimization
- Indexes and caching demonstrate measurable performance gains
- Report clearly communicates methodology and findings

**User Story 4.2**

> As a developer, I want to explore storing customer feedback or logs in a NoSQL format so that unstructured data can be efficiently handled.

**Acceptance Criteria:**
- NoSQL data model created for reviews or logs
- Justification provided for why NoSQL is suitable for the use case
- Optional implementation comparison included in performance report

---

#### Epic 5: Reporting and Documentation

**User Story 5.1**

> As a project contributor, I want to produce documentation and reports so that the project can be reviewed, reused, or extended.

**Acceptance Criteria:**
- ERD diagrams and database documentation included
- SQL scripts and sample data provided
- A README file describes setup, dependencies, and execution steps

---

### Technical Requirements

#### Database
- Use **MySQL** or **PostgreSQL** for the relational database implementation
- Database schema normalized to **Third Normal Form (3NF)**
- Include at least the following entity groups: `Users`, `Products`, `Categories`, `Orders`, `OrderItems`, `Reviews`, `Inventory`
- Define indexes on high-frequency columns (e.g., product name, category ID, order user ID)
- Implement foreign keys to maintain referential integrity

#### Application Layer (JavaFX + JDBC)
- Use **JavaFX** for user interaction: product listing, searching, CRUD operations, and reporting
- Database access implemented using **JDBC** with parameterized queries to prevent SQL injection
- Logical separation of concerns: `Controller → Service → DAO`
- In-memory structures (e.g., `Map`, `List`) used to cache and sort results
- Include an admin panel for product management and performance monitoring

#### Data Structures & Algorithms Integration
- **Hashing / Caching:** Use in-memory data structures to speed up lookups
- **Sorting & Searching:** Apply appropriate algorithms for ordering and filtering data
- **Indexing Concept:** Explain how in-memory structures mirror database index logic
- **Performance Measurement:** Demonstrate efficiency improvements from optimization efforts

---

### Deliverables

| Deliverable | Description |
|---|---|
| Database Design Document | Conceptual, logical, and physical models with ERDs and explanations |
| SQL Implementation Script | Scripts for creating tables, constraints, indexes, and inserting sample data |
| JavaFX Application | Functional interface that performs CRUD, search, and reporting using JDBC |
| Performance Report | Comparative analysis showing before/after optimization metrics (indexing, caching) |
| NoSQL Design *(Optional)* | Documented schema or implementation for storing unstructured data (e.g., reviews) |
| README File | Setup guide, dependencies, how to run SQL scripts, and usage instructions |
| Testing Evidence | Screenshots or reports showing correct query results and validation outcomes |

---

### Evaluation Criteria

| Category | Evaluation Criteria | Points |
|---|---|---|
| Database Design | Conceptual, logical, and physical models are complete, normalized (3NF), and well-documented with ERDs | 25 |
| SQL Implementation | SQL schema is syntactically correct, includes constraints, sample data, indexes, and supports complex queries | 20 |
| JavaFX + JDBC Integration | Functional CRUD operations, UI usability, safe JDBC handling, and error feedback are correctly implemented | 20 |
| DSA Application | Clear use of caching, sorting, and searching with performance justification and accurate mapping to indexing concepts | 15 |
| Performance Optimization | Performance gains demonstrated through timing, analysis, and documentation | 10 |
| Documentation & Code Quality | README completeness, code organization, comments, and adherence to clean coding practices | 10 |
| **Total** | | **100 pts** |
