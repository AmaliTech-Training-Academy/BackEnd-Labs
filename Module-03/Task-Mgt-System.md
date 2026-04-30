# Task Management System


---

## Project Objectives

By completing this project, you will be able to:

Design and implement type-safe data structures using Java Collections Framework and generics to efficiently manage complex student and grade data, selecting optimal collection types based on performance requirements and access patterns

Implement modern file I/O operations using NIO.2 API and Stream processing to handle multiple file formats (CSV, JSON, binary), with proper resource management and functional transformations for data import/export

Create comprehensive input validation using regular expressions to validate student IDs, email addresses, phone numbers, and other structured data formats, ensuring data integrity across the system

Design and implement thread-safe concurrent operations for background tasks such as batch processing, automated report generation, and real-time statistics updates using appropriate synchronization strategies and Executor framework

Optimize application performance by analyzing collection performance characteristics, implementing efficient data access patterns, and ensuring thread safety in multi-threaded operations

---

## What You'll Build

An enterprise-grade Student Grade Management System with advanced features including optimized collections, multi-format file handling, regex validation, concurrency, caching, auditing, and stream processing.

---

## Features

### Advanced Data Management

* HashMap for O(1) student lookup
* TreeMap for sorted GPA rankings
* HashSet for unique course tracking
* LinkedList for grade history
* PriorityQueue for task scheduling

### Multi-Format File Support

* CSV, JSON, Binary export/import
* NIO.2 Path and Files API
* Streaming for large files

### Regex-Based Validation

* Student ID, Email, Phone, Date, Course Code validation
* Centralized ValidationUtils class

### Concurrent Processing

* FixedThreadPool for batch reports
* CachedThreadPool for stats
* ScheduledExecutorService for tasks

### Real-Time Dashboard

* Live statistics updates
* Background daemon thread
* Thread-safe data structures

### Caching System

* ConcurrentHashMap-based cache
* LRU eviction policy
* Cache statistics tracking

### Audit Trail

* Async logging
* Thread-safe logging queue
* Log rotation support

---

## Console Output Examples

### Main Menu

```
╔════════════════════════════════════════════╗ 
║   STUDENT GRADE MANAGEMENT - MAIN MENU     ║ 
╚════════════════════════════════════════════╝ 
```

### Features include:

* File export/import
* Real-time dashboard
* Batch processing
* Regex search
* Scheduled tasks

---

## User Stories

### US-1: Advanced Data Management

Use optimized collections for performance:

* HashMap → student lookup
* TreeMap → GPA ranking
* HashSet → unique courses

### US-2: Multi-Format File Operations

* CSV, JSON, Binary support
* NIO.2 streaming
* WatchService integration

### US-3: Regex Validation

Patterns:

* STU\d{3}
* Email regex
* Phone formats
* Date YYYY-MM-DD

### US-4: Concurrent Batch Reports

* ThreadPoolExecutor
* Progress tracking
* Performance comparison

### US-5: Real-Time Dashboard

* Auto-refresh every 5 seconds
* Background thread updates

### US-6: Scheduled Tasks

* Daily GPA calculation
* Hourly stats refresh
* Weekly reports

### US-7: Pattern Search

* Regex-based filtering
* Domain search
* ID search

### US-8: Caching System

* LRU cache
* Hit/miss tracking
* Thread-safe access

### US-9: Audit Trail

* Async logging
* Thread ID tracking
* Log rotation

### US-10: Stream Processing

* map, filter, reduce
* parallelStream
* Files.lines()

---

## Architecture

### Collections

* HashMap → Students
* TreeMap → GPA rankings
* ArrayList → ordered data
* HashSet → uniqueness
* ConcurrentHashMap → cache

### Thread Pools

* FixedThreadPool → reports
* CachedThreadPool → stats
* ScheduledThreadPool → tasks
* SingleThreadExecutor → logging

---

## Testing Requirements

* 25+ unit tests
* 10+ integration tests
* 85%+ coverage
* Concurrency testing
* Regex validation tests
* Stream processing tests

---

## Git Workflow

### Branch Strategy

* main
* develop
* feature branches

### Required Commits

* 30+ commits
* Conventional commits
* Feature-based structure

---

## Minimum Requirements

### Collections

* HashMap O(1) lookup
* TreeMap sorting
* HashSet uniqueness

### File I/O

* NIO.2 usage
* Streaming files
* Multi-format support

### Concurrency

* Thread-safe operations
* ExecutorService usage

### Regex

* Precompiled patterns
* ValidationUtils class

### Streams

* Functional operations
* Parallel processing

---

## Performance Benchmarks

* HashMap vs ArrayList lookup
* Sequential vs parallel streams
* File I/O comparisons
* Thread pool efficiency

---

## Final Requirement

All features must be fully implemented, tested, and documented with proper Git workflow and performance analysis.
