# E-Commerce Analytics Data Pipeline

**Assessment:** Database Fundamentals  
**Complexity:** Medium  
**Estimated Time:** 6–10 hours

---

## Objectives

By completing this lab, learners should be able to:

- Design a normalized relational database schema for an e-commerce platform
- Write Python scripts using `psycopg2` for transactional CRUD operations
- Integrate NoSQL (Redis, MongoDB) and advanced SQL (`JSONB`) storage
- Write complex SQL queries with window functions and CTEs
- Analyze and optimize query performance using `EXPLAIN ANALYZE` and indexing

---

## Description

Build a data processing and analytics pipeline for a fictional e-commerce store.

You will:

- Design a normalized PostgreSQL schema for customers, products, and orders
- Write Python scripts to populate and manage data transactionally
- Use **Redis** for caching popular products
- Use **MongoDB** for user session data
- Use **PostgreSQL JSONB** for product metadata
- Write and optimize analytical SQL queries for reporting

---

## Implementation Details

### 1. Database Modeling and Normalization

- Create ER diagram for customers, products, orders, order_items
- Write `CREATE TABLE` scripts in 3rd Normal Form (3NF)
- Define primary keys, foreign keys, and constraints
- Document normalization decisions

### 2. Python Database Connectivity (DB-API)

- Use `psycopg2` for PostgreSQL connection
- Implement connection pooling
- Write CRUD functions: `create_order()`, `add_product()`, `get_customer_orders()`
- Use parameterized queries (prevent SQL injection)
- Use transactions for order creation (ACID compliance)

### 3. Integrating SQL and NoSQL

- **PostgreSQL JSONB** → product metadata (sizes, colors, etc.)
- **Redis** → caching top 10 best-selling products
- **MongoDB** → user session/cart data using `pymongo`

### 4. Complex Queries and Optimization

- Use window functions (`RANK()`) for product ranking
- Use CTEs for revenue per customer
- Use `EXPLAIN ANALYZE` for query inspection
- Add B-tree index on `customer_id` and measure improvement
- Add GIN index on JSONB and query metadata efficiently

---

## Milestones

| Day | Focus | Tasks |
|---|---|---|
| Day 1 | Database Design and Setup | Design ER diagram and schema, set up PostgreSQL (Docker), create tables using Python script |
| Day 2 | Core Data Operations | Implement CRUD functions, implement transactional order processing, insert sample data |
| Day 3 | NoSQL and Advanced SQL | Integrate Redis and MongoDB, write window function and CTE queries, add JSONB operations |
| Day 4 | Performance Optimization | Run `EXPLAIN ANALYZE`, add indexes (B-tree, GIN), document performance improvements |

---

## Grading Criteria (100 Points)

| Criteria | Points |
|---|---|
| Feature Implementation | 20 |
| Code Quality & Structure | 15 |
| Best Practices & Patterns | 15 |
| Testing & Validation | 20 |
| Documentation & Comments | 10 |
| Final Integration & Output Quality | 20 |

---

## Submission Requirements

- Python 3.11+ application
- GitHub repository with full code
- `docker-compose.yml` (PostgreSQL, Redis, MongoDB)
- `requirements.txt`
- `README.md` with ER diagram, schema explanation, and optimization report
- SQL files (DDL + sample data)
- Loom video demonstrating the system
