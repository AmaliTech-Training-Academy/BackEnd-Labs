# Social Media Platform Data Backend

**Assessment:** Database Fundamentals  
**Complexity:** Medium  
**Estimated Time:** 6–10 hours

---

## Objectives

By completing this lab, learners should be able to:

- Design a normalized schema for a social media application
- Use `psycopg2` for transactional operations (e.g., following a user)
- Combine SQL and NoSQL for different data types
- Write complex queries for user feeds and trending posts
- Optimize query performance for high-read workloads

---

## Description

Build the data backend for a social media platform.

You will design a normalized PostgreSQL schema for:

- Users
- Posts
- Comments
- Followers

Python scripts will handle:

- Creating posts
- Following users (transactional operations)

You will also use:

- **Redis** for caching user timelines
- **MongoDB** for activity logs
- **PostgreSQL JSONB** for post metadata

Main focus: building and optimizing feed generation queries.

---

## Implementation Details

### 1. Modeling

- Design 3NF schema for users, posts, comments, followers
- Create ER diagram

### 2. Python Connectivity

- Use `psycopg2` with connection pooling
- "Follow user" must be transactional (atomic updates)
- Use parameterized queries everywhere

### 3. SQL & NoSQL Integration

- **PostgreSQL:** store post metadata (tags, location) using `JSONB`
- **Redis:** cache user timelines
- **MongoDB:** store activity logs (likes, follows, etc.)

### 4. Complex Queries & Performance

- Use CTEs and JOINs to generate user timeline
- Use `ROW_NUMBER()` for pagination
- Use `EXPLAIN ANALYZE` to optimize feed query
- Add composite B-tree indexes on the followers table

---

## Milestones

| Day | Tasks |
|---|---|
| Day 1 | Database schema design and setup |
| Day 2 | Core user actions with Python transactions |
| Day 3 | Redis caching and MongoDB logging |
| Day 4 | Feed query building and optimization |

---

## Grading & Submission

Same structure as Lab 1, with emphasis on:

- Feed generation query performance
- Correct transactional follow feature
