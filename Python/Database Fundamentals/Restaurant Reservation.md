# Restaurant Reservation and Review System Backend

**Assessment:** Database Fundamentals  
**Complexity:** Medium  
**Estimated Time:** 6–10 hours

---

## Objectives

By completing this lab, learners should be able to:

- Design a normalized database schema for a reservation system
- Implement transactional reservation booking using Python + `psycopg2`
- Combine SQL and NoSQL for structured and unstructured data
- Write and optimize complex location-based analytical queries
- Use window functions and `EXPLAIN ANALYZE` for performance tuning

---

## Description

Build the backend for a restaurant reservation and review system.

You will design a normalized PostgreSQL schema for:

- Restaurants
- Customers
- Reservations
- Reviews

Core feature: a transactional Python function that books a reservation while ensuring table availability.

The system also integrates:

- **Redis** → caching table availability
- **MongoDB** → unstructured customer feedback/reviews
- **PostgreSQL JSONB** → menus, opening hours

---

## Implementation Details

### 1. Database Modeling

- Design a 3NF schema for restaurants, tables, customers, reservations, reviews
- Create an ER diagram

### 2. Python + Database (psycopg2)

- Use connection pooling
- Reservation booking must be an atomic transaction:
  - Check table availability
  - Insert reservation only if available
- Use parameterized queries (no SQL injection risk)

### 3. SQL + NoSQL Integration

**PostgreSQL:**
- Store menus and opening hours in `JSONB` columns

**Redis:**
- Cache table availability for specific time slots

**MongoDB:**
- Store long-form customer feedback and reviews

### 4. Complex Queries + Performance

- `RANK()` → rank restaurants by average review score per city
- CTE → find available tables for a given time + party size
- `EXPLAIN ANALYZE` → optimize availability query
- Indexing:
  - Index time slots + table capacity
  - Consider `GiST` index for location-based search

---

## Milestones

| Day | Tasks |
|---|---|
| Day 1 | Schema design + database setup |
| Day 2 | Implement transactional reservation logic |
| Day 3 | Integrate Redis + MongoDB |
| Day 4 | Write + optimize analytical queries |

---

## Grading & Submission

Same structure as Lab 1, with focus on:

- Correct transactional reservation logic
- Query performance + optimization effectiveness
