# Online Learning Platform Data Service

**Assessment:** Database Fundamentals  
**Complexity:** Medium  
**Estimated Time:** 6–10 hours

---

## Objectives

By completing this lab, learners should be able to:

- Model a normalized database for an online learning platform
- Use `psycopg2` for transactional student enrollment management
- Integrate SQL and NoSQL for different platform components
- Write complex queries for progress tracking and analytics
- Optimize queries for dashboard-style performance

---

## Description

Build the backend data service for an online learning platform.

You will design a normalized PostgreSQL schema for:

- Students
- Courses
- Modules
- Lessons
- Enrollments

Python scripts will handle:

- Course enrollment (transactional and atomic)
- Progress tracking

You will also use:

- **Redis** for caching student progress
- **MongoDB** for discussion forum data
- **PostgreSQL JSONB** for quiz data

Main focus: powering a student dashboard with optimized queries.

---

## Implementation Details

### 1. Modeling

- Design 3NF schema for students, courses, modules, lessons, enrollments
- Create ER diagram

### 2. Python Connectivity

- Use `psycopg2` with connection pooling
- Enrollment process must be transactional (prerequisite check + enrollment insert)

### 3. SQL & NoSQL Integration

- **PostgreSQL:** store quizzes using `JSONB`
- **Redis:** cache course completion percentage per student
- **MongoDB:** store forum discussion threads

### 4. Complex Queries & Performance

- Use `GROUP BY` + subqueries for completion percentage per course
- Use `LAG()` window function for lesson completion timing
- Use `EXPLAIN ANALYZE` to optimize dashboard queries
- Add indexes for performance improvement

---

## Milestones

| Day | Tasks |
|---|---|
| Day 1 | Database design, DDL, and setup |
| Day 2 | Enrollment + progress tracking (transactions) |
| Day 3 | Redis, MongoDB, JSONB integration |
| Day 4 | Dashboard query optimization |

---

## Grading & Submission

Same structure as Lab 1, focused on:

- Correctness of progress calculations
- Correctness of transactional enrollment logic
