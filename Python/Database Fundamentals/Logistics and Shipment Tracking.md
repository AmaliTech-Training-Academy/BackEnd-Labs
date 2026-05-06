# Logistics and Shipment Tracking Backend

**Assessment:** Database Fundamentals  
**Complexity:** Medium  
**Estimated Time:** 6–10 hours

---

## Objectives

By completing this lab, learners should be able to:

- Design and normalize a relational schema for a logistics system
- Implement atomic transactional updates for package status using Python + `psycopg2`
- Integrate SQL and NoSQL for optimal data handling
- Write and optimize complex tracking queries using CTEs and window functions
- Use `EXPLAIN ANALYZE` and composite indexing for performance tuning

---

## Description

Build the backend data service for a shipment tracking company.

**Core system** — a normalized PostgreSQL database that stores:

- Packages
- Customers
- Shipments
- Tracking events
- Locations

**Python service responsibilities:**

- Process incoming scan events from warehouses/drivers
- Update package status transactionally
- Maintain real-time tracking data

**NoSQL integration:**

- **Redis** → fast access to latest package status
- **MongoDB** → raw scanner event logs for auditing

Main challenge: build a high-performance query that reconstructs full package history efficiently.

---

## Implementation Details

### 1. Database Modeling & Normalization

- Design ER diagram for: `Packages`, `Customers`, `Shipments`, `TrackingEvents`, `Locations`
- Ensure 3NF normalization
- Define primary keys, foreign keys, and constraints

### 2. Python + Transactions (psycopg2)

- Use connection pooling
- Implement: `process_tracking_scan(package_id, location, status)`

This function must:
- Insert into `TrackingEvents`
- Update `Packages.current_status`
- Execute as a single ACID transaction

- Use parameterized queries (security requirement)

### 3. SQL + NoSQL Integration

**PostgreSQL:**
- Core relational data storage
- `package_metadata` JSONB field (fragile, requires_signature, etc.)

**Redis:**
- Cache latest tracking status
- Key format: `package:<tracking_id>:status`
- Value: `{"status": "In Transit", "location": "City, ST"}`

**MongoDB:**
- Store raw scanner event logs
- Include scanner ID, timestamps, metadata

### 4. Complex Queries + Performance

- Use CTE to reconstruct full tracking history of a package
- Use `LAG()` to compute time between tracking events
- Run `EXPLAIN ANALYZE` on large datasets
- Create composite index: `(package_id, event_timestamp)` on `TrackingEvents`
- Compare performance before/after indexing

---

## Milestones

| Day | Tasks |
|---|---|
| Day 1 | ER diagram + schema design, PostgreSQL DDL setup, Docker environment (Postgres, Redis, MongoDB) |
| Day 2 | Implement `process_tracking_scan` transaction, test scan processing logic, seed database with sample data |
| Day 3 | Redis caching implementation, MongoDB logging integration, read/write utility functions |
| Day 4 | Final tracking history query (CTE + LAG), `EXPLAIN ANALYZE` benchmarking, performance documentation |

---

## Grading Criteria (100 Points)

| Criteria | Points | Description |
|---|---|---|
| Feature Implementation | 20 | Transactional updates + NoSQL integration work correctly |
| Code Quality & Structure | 15 | Clean Python structure + readable SQL |
| Best Practices & Patterns | 15 | Proper normalization, ACID transactions, caching strategy |
| Testing & Validation | 20 | Correct tracking history query + proven performance improvement |
| Documentation & Comments | 10 | Clear ER diagram + well-written README |
| Final Integration & Output Quality | 20 | System works end-to-end as a complete pipeline |

---

## Submission Requirements

- Python 3.11+ application
- GitHub repository
- `docker-compose.yml` (Postgres, Redis, MongoDB)
- `requirements.txt`
- SQL files (DDL + sample data)
- `README.md` with:
  - ER diagram
  - Schema explanation
  - `EXPLAIN ANALYZE` performance report
- Loom video showing scan processing + history query
