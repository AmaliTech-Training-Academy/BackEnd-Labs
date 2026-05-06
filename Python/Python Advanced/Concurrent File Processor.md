# Concurrent File Processor with Threading & Multiprocessing

**Assessment:** Python Advanced  
**Complexity:** Medium  
**Estimated Time:** 6–10 hours

---

## Objectives

By completing this lab, learners should be able to:

- Understand threading fundamentals and the GIL (Global Interpreter Lock)
- Implement thread-safe operations using `Lock`, `RLock`, `Semaphore`
- Use `Queue` for thread-safe communication
- Apply `concurrent.futures` (`ThreadPoolExecutor`, `ProcessPoolExecutor`)
- Understand when to use threading vs. multiprocessing
- Implement basic async patterns with `asyncio` (introduction level)

---

## Description

Build a **Concurrent File Processor** that downloads files from URLs, processes them (image resize, text analysis, data conversion), and saves results.

You'll implement three versions: sequential, threaded (for I/O-bound tasks), and multiprocessed (for CPU-bound tasks). Learn thread synchronization using locks and queues. Use `concurrent.futures` for clean concurrent code. Add a simple `asyncio` version for comparison. Measure and compare performance across approaches.

---

## Implementation Details

### 1. Threading with the `threading` Module

- Create worker threads for file downloads
- Use `Lock` to protect shared state (progress counter)
- Use `Queue` for distributing work to threads
- Implement thread-safe logging
- Understand GIL limitations for CPU-bound work

### 2. Thread Synchronization

- Use `Lock` for critical sections
- Use `Semaphore` to limit concurrent operations
- Use `Event` for signaling between threads
- Demonstrate race conditions without locks (for learning)

### 3. concurrent.futures

- Implement `ThreadPoolExecutor` for I/O-bound file downloads
- Implement `ProcessPoolExecutor` for CPU-bound image processing
- Use `as_completed()` and `map()` patterns
- Handle exceptions in worker threads/processes

### 4. Multiprocessing

- Use `multiprocessing.Pool` for parallel CPU work
- Share data using `Queue` or `Manager`
- Understand when multiprocessing beats threading

### 5. Basic asyncio Introduction

- Convert download logic to `async`/`await` pattern
- Create simple event loop
- Use `asyncio.gather()` for concurrent downloads
- Compare with threading approach

### 6. Performance Measurement

- Time each approach for different workloads
- Plot results showing threading vs. multiprocessing trade-offs
- Document GIL impact

---

## Milestones

| Days | Focus | Tasks |
|---|---|---|
| Day 1–2 | Sequential Baseline | Implement sequential file processor, measure baseline performance, prepare test dataset (20+ files) |
| Day 3–5 | Threading Implementation | Add threading with `Queue`, implement locks for thread safety, use `ThreadPoolExecutor` |
| Day 6–7 | Multiprocessing | Implement `ProcessPoolExecutor` version, compare threading vs. multiprocessing performance, document GIL observations |
| Day 8–9 | Basic asyncio & Testing | Create simple asyncio download version, write tests for thread safety, generate performance comparison report |

---

## Grading Criteria (100 Points)

| Criteria | Points | Description |
|---|---|---|
| Feature Implementation | 20 | All three approaches working, file processing correct |
| Code Quality & Structure | 15 | Clean threading code, proper resource cleanup |
| Best Practices & Patterns | 15 | Correct lock usage, appropriate executor choice, thread safety |
| Testing & Validation | 20 | Thread safety tests, performance benchmarks, race condition demos |
| Documentation & Comments | 10 | Threading concepts explained, GIL impact documented |
| Final Integration & Output Quality | 20 | Performance graphs, comparison analysis, demo video |

---

## Submission Requirements

- Python 3.11+ with `concurrent.futures`, `asyncio`
- GitHub repo with test files
- `README.md` with:
  - Threading vs. multiprocessing decision guide
  - GIL explanation
  - Performance comparison table/graph
- Performance benchmark script
- Loom video showing concurrent execution
