# Async Web Scraper with asyncio Fundamentals

**Assessment:** Python Advanced  
**Complexity:** Medium  
**Estimated Time:** 6–10 hours

---

## Objectives

By completing this lab, learners should be able to:

- Understand asyncio event loop and coroutine basics
- Implement async/await patterns for I/O-bound tasks
- Use `asyncio.gather()` and `asyncio.create_task()` for concurrency
- Apply decorators to async functions
- Use generators and iterators with async operations
- Compare async vs threading performance

---

## Description

Build an **Async Web Scraper** that fetches multiple web pages concurrently, extracts data using regex, and stores results in JSON format.

You will implement async HTTP requests, process responses with async generators, and coordinate tasks using `asyncio`.

You will also:

- Apply decorators for retry logic and rate limiting
- Use `pathlib` for output management
- Use functional programming for data processing
- Compare async performance with threaded and sequential approaches

---

## Implementation Details

### 1. asyncio Basics

- Create event loop and run coroutines
- Define `async def` functions
- Use `await` for asynchronous operations
- Understand coroutine vs function

### 2. Concurrent HTTP Requests

- Use `aiohttp` library for async HTTP
- Fetch multiple URLs concurrently with `asyncio.gather()`
- Use `asyncio.create_task()` for task management
- Handle timeouts with `asyncio.wait_for()`

### 3. Async Generators

- Implement async generator functions using `yield`
- Process responses asynchronously
- Use `async for` loops

### 4. Decorators for Async Functions

- Create `@retry` decorator for failed requests
- Create `@rate_limit` decorator to throttle requests
- Apply decorators to async functions

### 5. Data Processing

- Use regex to extract structured data
- Use `map` and `filter` for transformations
- Write results to JSON using async file I/O

### 6. Performance Comparison

- Implement sequential version
- Implement threaded version
- Benchmark async vs threading vs sequential

---

## Milestones

| Days | Focus | Tasks |
|---|---|---|
| Day 1–2 | asyncio Fundamentals | Set up asyncio event loop, implement basic async HTTP requests, fetch single URL asynchronously |
| Day 3–4 | Concurrent Fetching | Implement `asyncio.gather()` for multiple URLs, add error handling and timeouts, test with 20+ URLs |
| Day 5–6 | Async Generators & Decorators | Implement async generators, add retry and rate limit decorators, integrate into scraping pipeline |
| Day 7–8 | Data Processing & Comparison | Add regex extraction, build sequential and threaded versions, generate performance report |

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

- Python 3.11+ with `aiohttp` and `asyncio`
- GitHub repository
- `requirements.txt`

`README.md` must include:

- `asyncio` explanation
- Performance comparison (async vs threading vs sequential)
- Setup instructions
- Benchmark results
- Sample JSON output

> **Also required:** Loom video showing concurrent execution
