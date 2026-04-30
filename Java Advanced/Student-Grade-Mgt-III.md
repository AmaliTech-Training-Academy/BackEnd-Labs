# Student Grade Management System -Advanced

---

# Project Objectives
## Time Estimate : 6–7 hours

By completing this project, you will be able to:

* Design and implement type-safe data structures using Java Collections Framework and generics to efficiently manage complex student and grade data, selecting optimal collection types based on performance requirements and access patterns
* Implement modern file I/O operations using NIO.2 API and Stream processing to handle multiple file formats (CSV, JSON, binary), with proper resource management and functional transformations for data import/export
* Create comprehensive input validation using regular expressions to validate student IDs, email addresses, phone numbers, and other structured data formats, ensuring data integrity across the system
* Design and implement thread-safe concurrent operations for background tasks such as batch processing, automated report generation, and real-time statistics updates using appropriate synchronization strategies and Executor framework
* Optimize application performance by analyzing collection performance characteristics, implementing efficient data access patterns, and ensuring thread safety in multi-threaded operations

---

# What You’ll Build

An enterprise-grade Student Grade Management System with:

## New Features

### Advanced Data Management

* HashMap for O(1) student lookup
* TreeMap for sorted GPA rankings
* HashSet for unique course tracking

### Multi-Format File Support

* CSV, JSON, Binary export/import using NIO.2

### Regex-Based Validation

* Student ID, email, phone, date, course codes

### Concurrent Report Generation

* Thread pools for batch processing

### Real-Time Statistics Dashboard

* Background thread updates every 5 seconds

### Automated Grade Processing

* Scheduled GPA updates & notifications

### Advanced Search with Regex

* Pattern-based student queries

### Batch Operations

* Parallel bulk processing

### Data Caching System

* Thread-safe caching with eviction policy

### Audit Trail

* Concurrent logging system

---

# Console Output Examples

## Screenshot 1: Main Menu

```text
╔════════════════════════════════════════════╗
║   STUDENT GRADE MANAGEMENT - MAIN MENU     ║
║          [Advanced Edition v3.0]           ║
╚════════════════════════════════════════════╝
```

(Full menu retained in implementation)

---

## Screenshot 2: Multi-Format Export

```text
EXPORT GRADE REPORT (Multi-Format)
Processing with NIO.2 Streaming...
CSV Export completed
JSON Export completed
Binary Export completed
```

---

## Screenshot 3: Regex Validation

```text
✗ INVALID Student ID format
✓ Valid Student ID: STU123
```

---

## Screenshot 4: Real-Time Dashboard

```text
REAL-TIME STATISTICS DASHBOARD
Active Threads: 5
Cache Hit Rate: 87.3%
Grade Distribution updating live
```

---

## Screenshot 5: Batch Processing

```text
Concurrent Batch Reports
Performance Gain: 10x faster
Thread Pool: 6 threads active
```

---

## Screenshot 6: Pattern Search

```text
SEARCH RESULTS (12 found)
@university.edu domain filter applied
```

---

## Screenshot 7: Scheduled Tasks

```text
Daily GPA Recalculation
Next run: 03:30 AM
Status: Scheduled
```

---

## Screenshot 8: Performance Monitor

```text
HashMap Access: 0.8ms (O(1))
TreeMap Sorting: O(log n)
Cache Hit Rate: 87.3%
```

---

# User Stories

## US-1: Collections Optimization

* HashMap, TreeMap, HashSet usage
* Big-O complexity required

## US-2: Multi-Format File I/O

* CSV, JSON, Binary support
* NIO.2 streaming required

## US-3: Regex Validation

* STU\d{3}, email, phone, date patterns

## US-4: Concurrent Batch Reports

* FixedThreadPool (2–8 threads)

## US-5: Real-Time Dashboard

* Background thread updates every 5s

## US-6: Scheduled Tasks

* ScheduledExecutorService

## US-7: Pattern Search

* Regex-based filtering

## US-8: Caching System

* ConcurrentHashMap + LRU

## US-9: Audit Trail

* Thread-safe logging

## US-10: Stream Processing

* map, filter, reduce, collect

---

# Architecture Requirements

## Collections

* HashMap<StudentID, Student>
* TreeMap<GPA, Students>
* HashSet<Courses>
* LinkedList<GradeHistory>
* PriorityQueue<Tasks>

## Threading

* FixedThreadPool (reports)
* CachedThreadPool (stats)
* ScheduledThreadPool (tasks)
* SingleThreadExecutor (logging)

---

# NIO.2 Requirements

* Path API usage
* Files.lines() streaming
* BufferedWriter
* Object serialization
* WatchService directory monitoring

---

# Regex Patterns

* Student ID: STU\d{3}
* Email validation
* Phone formats (multiple)
* Date: YYYY-MM-DD
* Course: ENG101 format

---

# Testing Requirements

## Unit Tests (25+)

* Collections
* Regex
* Streams
* File I/O

## Integration Tests (10+)

* Mock ExecutorService
* Mock file system

## Coverage

* Minimum 85%

---

# Git Workflow

## Branching

* main
* de
