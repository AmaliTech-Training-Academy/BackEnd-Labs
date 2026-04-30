
# Bank Account Management
---

## Project Overview

This lab builds directly on Week 2, enhancing the Bank Account Management System by introducing modern Java features:

- Migration from arrays to **Java Collections** for more efficient, scalable data management
- Integration of **Functional Programming** (Lambdas, Functional Interfaces, Method References, Streams API) for concise, functional-style data processing
- Implementation of **File I/O and NIO** (Path API) for persistent storage of accounts and transactions
- Use of **Regular Expressions (Regex)** for validating inputs (account numbers, emails, etc.)
- Introduction to **Concurrency Fundamentals** with threads and synchronized methods for thread-safe transactions

All data is now managed in-memory using Collections and processed via functional streams, then saved/loaded from text files. This lab prepares the foundation for future persistence using databases and multi-threaded service simulations.

---

## Project Objectives

By completing this lab, you will be able to:

- Use `ArrayList` and `HashMap` for efficient account and transaction storage
- Apply Lambdas, Streams, and Functional Interfaces to perform filtering, mapping, and reduction on collections
- Apply File I/O (NIO Paths & Files) for saving and loading account data persistently
- Implement Regex-based validation for customer info and account formats
- Demonstrate basic concurrency with threads and synchronized methods
- Maintain thread safety and avoid data corruption during concurrent transactions
- Design code that's modular, reusable, and ready for future database integration

---

## System Features Overview

### Feature 1: Collections Migration with Functional Programming
- Replace arrays with `ArrayList` and `HashMap<String, Account>`
- Implement efficient search, insert, and update operations
- Support sorting transactions by date or amount using comparators and Streams
- Use Lambda expressions for concise iteration and transformation of data

### Feature 2: File Persistence with Functional Stream Processing
- Save all accounts and transactions to files (`accounts.txt`, `transactions.txt`)
- Load data automatically on startup
- Use Java NIO `Files` and `Paths` APIs for reading/writing
- Process loaded data using Streams and Method References for mapping lines into `Account` and `Transaction` objects

### Feature 3: Regex Validation
- Validate account numbers (`ACC\d{3}`), emails, and phone numbers
- Display user-friendly errors for invalid input formats
- Centralize validation logic in `ValidationUtils`
- Optionally apply `Predicate` lambdas for dynamic validation rules

### Feature 4: Thread-Safe Concurrent Transactions
- Use `Thread` and `synchronized` to simulate multiple deposits/withdrawals
- Demonstrate concurrency by running simultaneous operations safely
- Prevent race conditions and data inconsistencies
- Optionally use parallel streams for batch transaction simulations

### Feature 5: Enhanced Console Experience
- Show data load/save confirmation messages
- Display thread activities in real time
- Maintain readable logs for file operations and thread actions

---

## Console UI Examples

### Main Menu (Extended)

```
╔════════════════════════════════════════════╗
║      BANK ACCOUNT MANAGEMENT SYSTEM        ║
╚════════════════════════════════════════════╝

Main Menu:
-----------
1. Manage Accounts
2. Perform Transactions
3. Generate Account Statements
4. Save/Load Data
5. Run Concurrent Simulation
6. Exit

Enter your choice: _
```

#### Collections Load Confirmation

```
Loading account data from files...

✓ 5 accounts loaded successfully from accounts.txt
✓ 20 transactions loaded from transactions.txt
```

#### Regex Validation Example

```
Enter customer email: john.smith@bank
❌ Error: Invalid email format. Please enter a valid address (e.g., name@example.com)

Enter customer email: john.smith@bank.com
✓ Email accepted!
```

#### Concurrent Deposit Simulation

```
Running concurrent transaction simulation...

Thread-1: Depositing $500 to ACC001
Thread-2: Depositing $300 to ACC001
Thread-3: Withdrawing $200 from ACC001

✓ Thread-safe operations completed successfully.
Final Balance for ACC001: $6,850.00
```

#### Functional Filtering Example

```java
transactions.stream()
    .filter(t -> t.getType().equals("DEPOSIT"))
    .sorted(Comparator.comparing(Transaction::getAmount).reversed())
    .forEach(System.out::println);
```

```
✓ Transactions filtered and sorted using Streams and Lambdas.
```

### File Save Confirmation

```
SAVING ACCOUNT DATA
─────────────────────────────────────────────
Accounts saved to accounts.txt
Transactions saved to transactions.txt
✓ File save completed successfully.
```

### Statement Generation (from Collections)

```
GENERATE ACCOUNT STATEMENT
─────────────────────────────────────────────
Enter Account Number: ACC003

Account: Emily Brown (Checking)
Current Balance: $1,240.00
Transactions (latest first):
─────────────────────────────────────────────
TXN019 | DEPOSIT    | +$300.00 | $1,240.00
TXN018 | WITHDRAWAL | -$200.00 | $940.00
─────────────────────────────────────────────
Net Change: +$100.00
```

### Application Exit

```
Thank you for using the Bank Account Management System!
Data automatically saved to disk.
Goodbye!
```

---

## Expected User Workflows

#### Workflow 1: Data Persistence Cycle
1. Start application → data auto-loads from files
2. User performs new transactions
3. User saves updates → confirms success
4. Restart → data persists correctly

#### Workflow 2: Collections and Functional Migration
1. Replace array-based logic with `ArrayList` and `HashMap`
2. Use Streams to perform filtering and sorting
3. Verify improved speed and concise syntax

#### Workflow 3: Regex Validation and Error Handling
1. Input invalid account/email → error displayed
2. Re-enter valid data → accepted
3. Verify all inputs conform to patterns

#### Workflow 4: Concurrent Transaction Simulation
1. Select "Run Concurrent Simulation"
2. Threads or parallel streams deposit/withdraw simultaneously
3. Observe interleaved logs
4. Verify final balances are accurate and thread-safe

---

## User Stories

#### Epic 1: Collections Migration and Functional Programming

**US-1.1: Replace Arrays with ArrayList and HashMap**
- Store accounts in `HashMap<String, Account>` for fast lookup
- Store transactions in `ArrayList`

**US-1.2: Implement Sorting and Search**
- Allow sorting transactions by date or amount using Streams and Lambdas

**Technical Requirements:** Use Java Collections API and Streams for filtering, mapping, and sorting.

---

#### Epic 2: File Persistence

**US-2.1: Save Accounts to File**
- Write account data to `accounts.txt` on exit

**US-2.2: Load Accounts on Startup**
- Read data using `Files.lines()` and map each line to an object using method references

**Technical Requirements:** Use `java.nio.file.Files`, `Paths`, and functional-style processing.

---

#### Epic 3: Regex Validation

**US-3.1: Validate Account Number and Email**
- Pattern: `ACC\d{3}`, Email: `^[A-Za-z0-9+_.-]+@[A-Za-z0-9.-]+$`
- Invalid inputs prompt error messages

**Technical Requirements:** Use `Pattern`, `Matcher`, and optionally `Predicate`s in `ValidationUtils`.

---

#### Epic 4: Concurrency and Thread Safety

**US-4.1: Simulate Concurrent Transactions**
- Run multiple threads executing deposits/withdrawals

**US-4.2: Ensure Thread Safety**
- Synchronize critical methods (e.g., `updateBalance()`)

**Technical Requirements:** Use `Thread`, `synchronized`, `Runnable`, or parallel streams.

---

#### Epic 5: Reporting and Persistence Validation

**US-5.1: Generate Statements from File-Loaded Data**
- Ensure transactions persist between sessions
- Display data from `ArrayList` and filter using Streams

**Technical Requirements:** Integrate I/O with functional processing for round-trip data consistency.

---

## Project Structure

```
bank-account-management-system/
│
├── src/
│   ├── Main.java
│   ├── models/
│   │   ├── Account.java
│   │   ├── SavingsAccount.java
│   │   ├── CheckingAccount.java
│   │   ├── Customer.java
│   │   ├── RegularCustomer.java
│   │   ├── PremiumCustomer.java
│   │   └── Transaction.java
│   │
│   ├── services/
│   │   ├── AccountManager.java
│   │   ├── TransactionManager.java
│   │   └── FilePersistenceService.java
│   │
│   └── utils/
│       ├── ValidationUtils.java
│       ├── ConcurrencyUtils.java
│       └── FunctionalUtils.java       # Helper for Lambdas and Stream operations
│
├── data/
│   ├── accounts.txt
│   └── transactions.txt
│
├── docs/
│   └── collections-architecture.md
│
└── README.md
```

---

### Implementation Phases

#### Phase 1: Collections & Functional Migration
- Replace arrays with `ArrayList` and `HashMap`
- Refactor `AccountManager` and `TransactionManager` using Streams for filtering and sorting
- Use lambdas for concise search and aggregation logic

#### Phase 2: File Persistence
- Implement save/load methods using `Files` and `Paths`
- Use `Files.lines()` and functional mapping for reading
- Handle I/O exceptions gracefully

#### Phase 3: Regex Validation
- Add regex checks for emails and account numbers
- Centralize patterns in `ValidationUtils`
- Display helpful error messages

#### Phase 4: Concurrency Integration
- Add threaded or parallel stream-based transaction simulation
- Mark `updateBalance()` as `synchronized`
- Log thread outputs to console

---

### Minimum Requirements Checklist

- [ ] Collections (`ArrayList` & `HashMap`) used for data management
- [ ] Functional Programming (Lambdas, Functional Interfaces, Streams) implemented
- [ ] File I/O implemented for saving/loading data
- [ ] Regex validation added for user inputs
- [ ] Basic concurrency implemented using Threads
- [ ] All Week 2 features retained and functional
- [ ] README documents Collections, Streams, and Concurrency usage

---

## Grading Rubric

| Criteria | Points | Excellent (90–100%) | Good (75–89%) | Satisfactory (60–74%) |
|---|---|---|---|---|
| Collections & Functional Migration | 20 | Collections fully implemented with Streams, Lambdas, and Functional Interfaces used efficiently | Partial integration or inconsistent usage | Minimal or incorrect functional logic |
| File Persistence | 20 | Robust file handling with functional-style I/O processing | Partial persistence | Minimal file logic |
| Regex Validation | 15 | Strong patterns and reusable validation | Works for key fields only | Limited regex use |
| Concurrency (Threads) | 15 | Thread-safe logic; optional parallel streams; synchronized methods used | Partial concurrency or missed synchronization | Single-threaded operations |
| Functionality & Stability | 10 | All features stable, efficient, and consistent | Minor bugs | Unstable logic |
| DSA (Use of Collections & Algorithms) | 10 | Efficient iteration, sorting, and functional algorithms | Logical structure | Inefficient loops |
| Documentation | 10 | Complete README and inline documentation | Partial coverage | Minimal documentation |
| **Total** | **100** | | | |

---

## Submission Requirements

**Deliverables:**

Public GitHub Repository with:
- Source Code (`/src`)
- Data Files (`/data`)
- README documenting Collections, Functional Programming, File I/O, Regex, and Concurrency
- Docs (`/docs/collections-architecture.md`)
- At least 6 commits reflecting feature progression (collections → functional → I/O → regex → threads)

**Submission Link:** *(Insert Google Form or LMS link here)*

---

### Testing the Application

#### Test Scenario 1: Collections and Functional Migration
- Run the application and perform account and transaction operations
- Confirm `ArrayList` and `HashMap` usage with Streams for search/sort

#### Test Scenario 2: File Persistence (Round-Trip)
- Create 2 accounts and 3 transactions
- Save data, restart program, and reload to verify data integrity

#### Test Scenario 3: Regex Validation
- Test invalid/valid emails and account numbers
- Confirm proper error messages

#### Test Scenario 4: Concurrent Deposit Simulation
- Run "Concurrent Simulation"
- Verify synchronized deposits and final balance accuracy

#### Test Scenario 5: Stream-Based Transaction Sorting
- Generate 10 transactions
- Sort by amount/date using Streams and Lambdas
- Confirm correct ordering

#### Test Scenario 6: Error Handling on File Access
- Delete `accounts.txt` and confirm auto-creation and no crash

#### Test Scenario 7: Persistence Verification with Threads
- Run threaded transactions, save data, reload, and verify consistency

#### Test Scenario 8: Functional Reduction Operation
- Use `reduce()` on transaction amounts to calculate total deposits
- Confirm computed totals match manual calculations

#### Test Scenario 9: Code Validation and Documentation
- Check indentation, naming conventions, and Javadoc completeness

---
---

## Module 3.2: Student Grade Management System

**Complexity:** Advanced
**Time Estimate:** 6–7 hours

---

### Objectives

By completing this project, you will be able to:

- Design and implement type-safe data structures using Java Collections Framework and generics to efficiently manage complex student and grade data, selecting optimal collection types based on performance requirements and access patterns
- Implement modern file I/O operations using NIO.2 API and Stream processing to handle multiple file formats (CSV, JSON, binary), with proper resource management and functional transformations for data import/export
- Create comprehensive input validation using regular expressions to validate student IDs, email addresses, phone numbers, and other structured data formats, ensuring data integrity across the system
- Design and implement thread-safe concurrent operations for background tasks such as batch processing, automated report generation, and real-time statistics updates using appropriate synchronization strategies and the Executor framework
- Optimize application performance by analyzing collection performance characteristics, implementing efficient data access patterns, and ensuring thread safety in multi-threaded operations

---

### What You'll Build

An enterprise-grade Student Grade Management System with:

#### New Features (Building on Labs 1 & 2)
- **Advanced Data Management** – Replace basic data structures with optimized collections (`HashMap` for O(1) student lookup, `TreeMap` for sorted grade reports, `HashSet` for unique course tracking)
- **Multi-Format File Support** – Import/export data in CSV, JSON, and binary formats using NIO.2 with streaming for large files
- **Regex-Based Validation** – Comprehensive input validation for emails, phone numbers, student IDs, course codes, and custom data formats
- **Concurrent Report Generation** – Generate multiple student reports simultaneously using thread pools
- **Real-Time Statistics Dashboard** – Background thread continuously updating class statistics with thread-safe operations
- **Automated Grade Processing** – Scheduled tasks for periodic grade calculations, GPA updates, and email notifications
- **Advanced Search with Regex** – Pattern-based search supporting complex queries
- **Batch Operations** – Process multiple operations concurrently (bulk grade updates, mass report generation, parallel statistics calculation)
- **Data Caching System** – Thread-safe cache for frequently accessed data with automatic invalidation
- **Audit Trail** – Concurrent logging of all operations with timestamps to file using thread-safe mechanisms

#### Technical Enhancements
- **Collections Optimization** – Strategic use of `ArrayList`, `LinkedList`, `HashMap`, `TreeMap`, `HashSet`, `TreeSet` based on use cases
- **Stream Processing** – Functional operations for data filtering, mapping, and aggregation
- **NIO.2 File Operations** – Modern file handling with `Path`, `Files`, and `WatchService` for monitoring
- **Thread Safety** – Synchronized collections, concurrent collections (`ConcurrentHashMap`), and proper locking mechanisms
- **Executor Framework** – Fixed, cached, and scheduled thread pools for different concurrent tasks
- **Performance Monitoring** – Track operation times, collection sizes, and thread pool metrics

---

### Console Output Examples

#### Screenshot 1: Enhanced Main Menu with Concurrent Operations

```
╔════════════════════════════════════════════╗
║   STUDENT GRADE MANAGEMENT - MAIN MENU     ║
║          [Advanced Edition v3.0]           ║
╚════════════════════════════════════════════╝

STUDENT MANAGEMENT
1. Add Student (with validation)
2. View Students
3. Record Grade
4. View Grade Report

FILE OPERATIONS
5. Export Grade Report (CSV/JSON/Binary)
6. Import Data (Multi-format support)      [ENHANCED]
7. Bulk Import Grades

ANALYTICS & REPORTING
8. Calculate Student GPA
9. View Class Statistics
10. Real-Time Statistics Dashboard         [NEW]
11. Generate Batch Reports                 [NEW]

SEARCH & QUERY
12. Search Students (Advanced)             [ENHANCED]
13. Pattern-Based Search                   [NEW]
14. Query Grade History                    [NEW]

ADVANCED FEATURES
15. Schedule Automated Tasks               [NEW]
16. View System Performance                [NEW]
17. Cache Management                       [NEW]
18. Audit Trail Viewer                     [NEW]

19. Exit

Background Tasks: ⚡ 3 active | 📊 Stats updating...

Enter choice: _
```

#### Screenshot 2: Multi-Format File Export

```
Enter choice: 5

EXPORT GRADE REPORT (Multi-Format)
─────────────────────────────────────────────

Enter Student ID: STU001

Student: STU001 - Alice Johnson (alice.j@university.edu)
Type: Regular Student | Phone: +1-555-0123
Total Grades: 12

Export Format:
1. CSV (Comma-Separated Values)
2. JSON (JavaScript Object Notation)
3. Binary (Serialized Java Object)
4. All formats

Select format (1-4): 4

Processing with NIO.2 Streaming...

✓ CSV Export completed
  File: alice_johnson_detailed.csv | Location: ./reports/csv/ | Size: 3.2 KB | Time: 45ms

✓ JSON Export completed
  File: alice_johnson_detailed.json | Location: ./reports/json/ | Size: 4.8 KB | Time: 62ms

✓ Binary Export completed
  File: alice_johnson_detailed.dat | Location: ./reports/binary/ | Size: 2.1 KB | Time: 38ms

📊 Export Performance Summary:
  Total Time: 145ms | Total Size: 10.1 KB | I/O Operations: 3 parallel writes

Press Enter to continue...
```

#### Screenshot 3: Regex-Based Input Validation

```
Enter choice: 1

ADD STUDENT (with validation)
─────────────────────────────────────────────

Enter Student ID: stu-001

✗ VALIDATION ERROR: Invalid Student ID format
  Pattern required: STU### (STU followed by exactly 3 digits)
  Examples: STU001, STU042, STU999
  Your input: stu-001

Enter Student ID: STU123
✓ Valid Student ID

Enter Student Name: John123

✗ VALIDATION ERROR: Invalid name format
  Pattern required: Only letters, spaces, hyphens, and apostrophes
  Your input: John123 (contains digits)

Enter Student Name: John Smith
✓ Valid Student Name

Enter Email Address: john.smith@uni

✗ VALIDATION ERROR: Invalid email format
  Pattern required: username@domain.extension
  Your input: john.smith@uni (missing valid extension)

Enter Email Address: john.smith@university.edu
✓ Valid Email Address

...

✓ Student added successfully!
  All inputs validated with regex patterns
  Student ID: STU123 | Name: John Smith
  Email: john.smith@university.edu | Type: Honors Student
```

#### Screenshot 4: Real-Time Statistics Dashboard

```
Enter choice: 10

REAL-TIME STATISTICS DASHBOARD
─────────────────────────────────────────────
Auto-refresh: Enabled (5 sec) | Thread: RUNNING
Press 'Q' to quit | 'R' to refresh now | 'P' to pause
─────────────────────────────────────────────

Last Updated: 2025-11-03 14:32:18

SYSTEM STATUS
─────────────────────────────────────────────
Total Students: 25 | Active Threads: 5
Cache Hit Rate: 87.3% | Memory Usage: 145 MB / 512 MB

LIVE STATISTICS
─────────────────────────────────────────────
Total Grades: 347 | Grades Added (last 5 min): 12
Average Processing Time: 23ms

Grade Distribution (Live):
90-100% (A):  ████████████████████░  45.2% (157 grades)
80-89%  (B):  ███████████░░░░░░░░░░  32.8% (114 grades)
70-79%  (C):  █████░░░░░░░░░░░░░░░░  15.6% (54 grades)
60-69%  (D):  ██░░░░░░░░░░░░░░░░░░░  4.9%  (17 grades)
0-59%   (F):  █░░░░░░░░░░░░░░░░░░░░  1.4%  (5 grades)

Current Statistics:
Mean: 83.7% (↑ 0.3% from last update) | Median: 85.0% | Std Dev: 9.8%

CONCURRENT OPERATIONS IN PROGRESS
─────────────────────────────────────────────
[████████░░] Batch Report Generation (80%) - 3 threads
[██████████] Statistics Calculation (100%) - COMPLETED
[████░░░░░░] Cache Refresh (40%) - 2 threads

Auto-refresh in: 3 seconds...
```

#### Screenshot 5: Concurrent Batch Report Generation

```
Enter choice: 11

GENERATE BATCH REPORTS
─────────────────────────────────────────────

Enter number of threads (1-8): 6

Initializing thread pool...
✓ Fixed Thread Pool created: 6 threads

Processing 25 student reports...

Thread-1: ████████████████████ STU001 ✓ (234ms)
Thread-2: ████████████████████ STU002 ✓ (198ms)
Thread-3: ████████████████████ STU003 ✓ (256ms)

Progress: [████████████████░░░░] 40% (10/25 completed)

✓ BATCH GENERATION COMPLETED!
  Total Reports: 25 | Successful: 25 | Failed: 0
  Total Time: 5.8 seconds | Avg Time per Report: 232ms
  Sequential (estimated): 58s | Concurrent (actual): 5.8s
  Performance Gain: 10x faster

Press Enter to continue...
```

#### Screenshot 6: Advanced Pattern-Based Search

```
Enter choice: 13

PATTERN-BASED SEARCH
─────────────────────────────────────────────

Search Type:
1. Email Domain Pattern (e.g., @university.edu)
2. Phone Area Code Pattern
3. Student ID Pattern (e.g., STU0**)
4. Name Pattern (regex)
5. Custom Regex Pattern

Select type (1-5): 1

Enter email domain pattern: @university.edu

Searching with regex: .*@university\.edu$
Processing 25 students...

SEARCH RESULTS (12 found)
─────────────────────────────────────────────
STU001 | Alice Johnson  | alice.j@university.edu
STU003 | Charlie Davis  | c.davis@university.edu
...

Pattern Match Statistics:
  Total Students Scanned: 25 | Matches Found: 12 (48%)
  Search Time: 45ms | Regex Complexity: O(n)
```

#### Screenshot 7: Scheduled Automated Tasks

```
Enter choice: 15

SCHEDULE AUTOMATED TASKS
─────────────────────────────────────────────

ACTIVE SCHEDULES
1. [DAILY]   Backup Database         | Next Run: 2025-11-04 02:00:00 | ✓ Success
2. [HOURLY]  Update Statistics Cache | Next Run: 2025-11-03 15:00:00 | ⚡ Running
3. [WEEKLY]  Generate Progress Reports| Next Run: 2025-11-04 08:00:00 | ✓ Success

TASK CONFIGURATION SUMMARY
Task: Daily GPA Recalculation
Schedule: Every day at 03:30 AM | Scope: All Students (25)
Threads: 4 | Notifications: Email + Log file

✓ Task scheduled successfully!
  Next Execution: 2025-11-04 03:30:00
```

#### Screenshot 8: System Performance Monitor

```
Enter choice: 16

SYSTEM PERFORMANCE MONITOR
─────────────────────────────────────────────

COLLECTION PERFORMANCE ANALYSIS
Data Structure         | Size  | Access Time    | Memory
HashMap<StudentID>     | 25    | 0.8ms (O(1))   | 12.4 KB
TreeMap<GradeSort>     | 347   | 2.3ms (O(log n))| 28.7 KB
ArrayList<Students>    | 25    | 1.2ms (O(1))   | 8.2 KB
ConcurrentHashMap      | 150   | 1.1ms (O(1))   | 18.9 KB

THREAD POOL PERFORMANCE
Pool Type         | Active | Max | Queue | Completed
FixedThreadPool   | 3/5    | 5   | 2     | 1,247
CachedThreadPool  | 2/∞    | 8   | 0     | 894
ScheduledPool     | 1/3    | 3   | 1     | 156

CACHE PERFORMANCE
Total Entries: 150 | Hit Rate: 87.3% | Miss Rate: 12.7%
Avg Hit Time: 0.3ms | Avg Miss Time: 18.7ms | Evictions: 23 (LRU policy)

RESOURCE UTILIZATION
CPU Usage:    ████████░░░░░░░░░░ 42%
Memory:       ████████████░░░░░░ 145 MB / 512 MB (28%)
Threads:      ████░░░░░░░░░░░░░░ 12 active / 50 max
```

---

### User Stories

#### US-1: Advanced Data Management with Optimized Collections (NEW)

> **As a** developer
> **I want to** use optimized collection types
> **So that** the system performs efficiently with large datasets

**Acceptance Criteria:**
- Use `HashMap<String, Student>` for O(1) student lookup by ID
- Use `TreeMap<Double, List<Student>>` for sorted GPA rankings
- Use `HashSet<String>` for tracking unique courses enrolled
- Use `ArrayList` for maintaining insertion order where needed
- Use `LinkedList` for frequent insertions/deletions in grade history
- Use `PriorityQueue` for task scheduling based on priority
- Implement custom `Comparator` for sorting students by multiple criteria
- All collection operations documented with Big-O complexity
- Performance comparison report showing improvement over Lab 2

#### US-2: Multi-Format File Operations with NIO.2 (NEW)

> **As a** teacher
> **I want to** import and export data in multiple formats
> **So that** I can integrate with other systems and tools

**Acceptance Criteria:**
- Support CSV, JSON, and binary serialization formats
- Use `java.nio.file.Files` and `Path` for all file operations
- Implement streaming for large CSV files (don't load entire file into memory)
- Use try-with-resources for proper resource management
- Handle file encoding (UTF-8) explicitly
- Implement file watching with `WatchService` to detect new import files
- All file operations must handle `IOException` with specific error messages
- Create separate directories for each format: `./data/csv/`, `./data/json/`, `./data/binary/`

#### US-3: Comprehensive Regex Input Validation (NEW)

> **As a** system administrator
> **I want** all user inputs validated with regex patterns
> **So that** data integrity is maintained throughout the system

**Acceptance Criteria:**

| Field | Pattern |
|---|---|
| Student ID | `STU\d{3}` |
| Email | `^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\.[a-zA-Z]{2,}$` |
| Phone (format 1) | `\(\d{3}\) \d{3}-\d{4}` |
| Phone (format 2) | `\d{3}-\d{3}-\d{4}` |
| Phone (format 3) | `\+1-\d{3}-\d{3}-\d{4}` |
| Phone (format 4) | `\d{10}` |
| Name | `^[a-zA-Z]+(['-\s][a-zA-Z]+)*$` |
| Date | `^\d{4}-\d{2}-\d{2}$` (YYYY-MM-DD) |
| Course Code | `^[A-Z]{3}\d{3}$` (e.g., MAT101) |
| Grade | `^(100\|[1-9]?\d)$` (0–100) |

- Compile regex patterns once and reuse (`Pattern.compile()`)
- Create `ValidationUtils` class with static methods for each pattern
- Show examples of valid input when validation fails

#### US-4: Concurrent Batch Report Generation (NEW)

> **As a** teacher
> **I want to** generate reports for multiple students simultaneously
> **So that** I can save time when processing large classes

**Acceptance Criteria:**
- Allow selection of 2–8 concurrent threads based on available processors
- Use `ExecutorService` with `FixedThreadPool` for parallel report generation
- Display progress bar showing completion status for each thread
- Show individual report generation time for each student
- Calculate total time and compare with estimated sequential processing time
- Ensure thread-safe file writing (no concurrent write conflicts)
- Properly shut down thread pool with timeout
- Handle exceptions in individual threads without affecting others

#### US-5: Real-Time Statistics Dashboard with Background Thread (NEW)

> **As a** teacher
> **I want to** see live class statistics that update automatically
> **So that** I can monitor class performance in real-time

**Acceptance Criteria:**
- Launch background daemon thread that calculates statistics every 5 seconds
- Display auto-refreshing dashboard with current statistics
- Allow manual refresh and pause/resume functionality
- Use thread-safe collections (`ConcurrentHashMap` or synchronized blocks)
- Properly terminate background thread when exiting dashboard
- Display cache hit rate and performance metrics

#### US-6: Scheduled Automated Tasks (NEW)

> **As a** system administrator
> **I want to** schedule recurring tasks to run automatically
> **So that** routine operations happen without manual intervention

**Acceptance Criteria:**
- Use `ScheduledExecutorService` for task scheduling
- Support daily, hourly, and weekly schedules
- Tasks: Daily GPA recalculation, Hourly statistics cache refresh, Weekly batch report generation, Daily database backup
- Display all active scheduled tasks with next execution time
- Persist schedules (survive application restart)
- Log all scheduled task executions with timestamps
- Properly shut down scheduler on application exit

#### US-7: Advanced Pattern-Based Search (NEW)

> **As a** teacher
> **I want to** search using regex patterns
> **So that** I can find students matching complex criteria

**Acceptance Criteria:**
- Search by email domain pattern, phone area code, student ID, and name patterns
- Allow custom regex pattern input
- Handle invalid regex patterns gracefully with error message
- Show distribution statistics (e.g., email domain breakdown)
- Support case-insensitive matching option
- Allow bulk operations on search results

#### US-8: Thread-Safe Caching System (NEW)

> **As a** developer
> **I want to** implement a caching system
> **So that** frequently accessed data loads faster

**Acceptance Criteria:**
- Implement `ConcurrentHashMap` for thread-safe cache
- Implement LRU (Least Recently Used) eviction policy
- Set maximum cache size (150 entries)
- Display hit rate, miss rate, average times, memory usage, and eviction count
- Background thread periodically refreshes stale cache entries

#### US-9: Concurrent Audit Trail (NEW)

> **As a** system administrator
> **I want** all operations logged with timestamps
> **So that** I can track system usage and debug issues

**Acceptance Criteria:**
- Log all operations: add student, record grade, generate report, search, etc.
- Use thread-safe logging mechanism (`synchronized` method or `ConcurrentLinkedQueue`)
- Each log entry includes: Timestamp (ISO 8601), Thread ID, Operation type, Execution time, Success/failure status
- Write logs to file asynchronously to avoid blocking main operations
- Implement log rotation (new file daily or when size exceeds 10MB)
- Ensure no log entries are lost during concurrent operations

#### US-10: Stream-Based Data Processing (NEW)

> **As a** developer
> **I want to** use Java Streams for data processing
> **So that** code is more readable and efficient

**Acceptance Criteria:**
- Use `filter()`, `map()`, `reduce()`, and `collect()` for data operations
- Implement `parallelStream()` for large datasets
- Process large CSV files line-by-line using `Files.lines()` stream
- Compare performance of sequential vs parallel stream processing
- Demonstrate: Find all honors students with GPA > 3.5; Group students by grade range; Calculate average grade per subject; Find top 5 students by average grade

---

### New Architecture Requirements

#### Collections Framework Design

**Student Management:**
```java
HashMap<String, Student> studentMap      // O(1) lookup by student ID
TreeMap<Double, List<Student>> gpaRankings // Auto-sorted by GPA
ArrayList<Student> studentList            // Maintains insertion order
HashSet<String> uniqueCourses             // O(1) membership testing
```

**Grade Management:**
```java
LinkedList<Grade> gradeHistory             // Per student, chronological
TreeMap<String, List<Grade>> subjectGrades // Organized by subject (sorted)
ConcurrentHashMap<String, Statistics> statsCache // Thread-safe cache
```

**Task Management:**
```java
PriorityQueue<Task> taskQueue              // Tasks ordered by priority
ConcurrentLinkedQueue<AuditEntry> auditLog // Thread-safe, non-blocking
```

#### Thread Safety Requirements

- Use `ConcurrentHashMap` for concurrent student lookups; synchronize modification operations
- Use `synchronized` blocks around file write operations; implement file locking for concurrent access
- Use `AtomicInteger` for counters; `AtomicLong` for timestamps
- Always use try-with-resources for `ExecutorService`; implement proper shutdown hooks

#### Executor Framework Usage

| Pool Type | Configuration | Use Case |
|---|---|---|
| Fixed Thread Pool | `Executors.newFixedThreadPool(5)` | Batch report generation (CPU-bound) |
| Cached Thread Pool | `Executors.newCachedThreadPool()` | On-demand statistics (short-lived) |
| Scheduled Thread Pool | `Executors.newScheduledThreadPool(3)` | Recurring background tasks |
| Single Thread Executor | `Executors.newSingleThreadExecutor()` | Sequential log file writing |

#### NIO.2 File Operations

```java
// Streaming large CSV files (memory efficient)
Files.lines(path)                             // Returns Stream<String>

// Buffered writing
Files.newBufferedWriter(path, StandardOpenOption.CREATE)

// Directory watching
WatchService watcher = FileSystems.getDefault().newWatchService()
```

#### Regex Pattern Design

```java
public class ValidationPatterns {
    public static final Pattern STUDENT_ID = Pattern.compile("STU\\d{3}");
    public static final Pattern EMAIL = Pattern.compile("^[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}$");
    // All patterns compiled once as static final and reused
}
```

---

### Testing Requirements

#### Required Test Classes

**`CollectionPerformanceTest`** – Test HashMap vs ArrayList lookup speed, TreeMap sorting, HashSet uniqueness, Big-O empirical verification, parallel vs sequential stream performance.

**`ConcurrencyTest`** – Test thread-safe collections under concurrent load, race conditions, deadlock prevention, thread pool shutdown, cache consistency.

**`FileOperationsTest`** – Test NIO.2 file reading with various sizes, streaming vs full load memory comparison, concurrent file access, UTF-8 encoding, mock file system.

**`RegexValidationTest`** – Test each pattern with 10+ valid and 10+ invalid inputs, edge cases (empty strings, special characters), pattern compilation performance.

**`StreamProcessingTest`** – Test filter/map/reduce operations, parallel stream correctness, lazy evaluation, sequential vs parallel performance comparison.

#### Test Coverage Requirements

| Scope | Target |
|---|---|
| Overall | 85%+ |
| Collections utility classes | 95%+ |
| Concurrent operations | 90%+ |
| Regex validation | 95%+ |
| File operations | 85%+ |
| Exception scenarios | 100% |

---

### Git Workflow Requirements

#### Branch Strategy

```
main (protected)
  └── develop
       ├── feature/advanced-collections
       ├── feature/nio2-file-operations
       ├── feature/regex-validation
       ├── feature/concurrent-reports
       ├── feature/realtime-dashboard
       ├── feature/scheduled-tasks
       ├── feature/pattern-search
       ├── feature/caching-system
       ├── feature/audit-trail
       └── feature/stream-processing
```

#### Commit Requirements (30+ minimum)

```
feat(collections): implement HashMap for O(1) student lookup
feat(nio2): add streaming CSV reader with Files.lines()
feat(regex): add comprehensive email validation pattern
feat(concurrent): implement batch report generation with FixedThreadPool
test(concurrency): add thread-safety tests for ConcurrentHashMap
perf(collections): optimize TreeMap usage for GPA rankings
fix(regex): correct phone pattern to support international format
```

---

### Minimum Requirements

**Collections & Data Structures**
- [ ] `HashMap` for O(1) student lookup implemented
- [ ] `TreeMap` for sorted GPA rankings implemented
- [ ] `HashSet` for unique course tracking implemented
- [ ] `LinkedList` for grade history implemented
- [ ] `PriorityQueue` for task scheduling implemented
- [ ] `ConcurrentHashMap` for thread-safe cache implemented
- [ ] Big-O complexity documented for all collections

**File Operations**
- [ ] NIO.2 `Path` and `Files` API used throughout
- [ ] CSV streaming with `Files.lines()` implemented
- [ ] JSON export/import implemented
- [ ] Binary serialization implemented
- [ ] Try-with-resources used for all I/O

**Regex Validation**
- [ ] All 8 patterns implemented and tested
- [ ] All patterns compiled once and reused
- [ ] Validation error messages display expected format

**Concurrency**
- [ ] `FixedThreadPool` for batch reports implemented
- [ ] `ScheduledExecutorService` for automated tasks implemented
- [ ] Real-time dashboard with background thread implemented
- [ ] Thread-safe operations verified (no race conditions)
- [ ] Proper `ExecutorService` shutdown implemented

**Testing**
- [ ] Minimum 25 unit tests
- [ ] Minimum 10 integration tests with mocking
- [ ] 85%+ code coverage achieved
- [ ] Performance benchmarks documented

---

### Grading Rubric

| Criteria | Points | What We're Looking For |
|---|---|---|
| Collections Framework | 15 | Appropriate types chosen, Big-O documented, efficient implementations, proper use of generics |
| Concurrency & Threading | 20 | Thread pools correctly configured, no race conditions, proper synchronization, `ExecutorService` managed, concurrent collections used |
| File I/O (NIO.2) | 15 | NIO.2 API used throughout, streaming for large files, try-with-resources, multiple format support, resource cleanup |
| Regex Validation | 10 | All patterns implemented correctly, compiled once, comprehensive validation, clear error messages |
| Stream Processing | 10 | Functional operations used appropriately, parallel streams for performance, memory-efficient processing |
| Testing | 15 | 85%+ coverage, meaningful tests, performance benchmarks, concurrency tests, mocking used |
| Git Workflow | 10 | 30+ commits, feature branches, conventional messages, pull requests documented |
| Code Quality | 5 | Clean code, thread safety documented, proper resource management, comprehensive JavaDoc |
| **Total** | **100** | |

---

### Testing the Application

#### Test Scenario 1: Collections Performance
1. Add 100 students; measure `HashMap` lookup vs `ArrayList` search
2. Add 500 more students; verify `HashMap` still O(1)
3. Check `TreeMap` auto-sorting for GPA rankings
4. Verify `HashSet` prevents duplicate course codes

#### Test Scenario 2: Concurrent Batch Reports
1. Add 25 students with grades; set thread count to 6
2. Monitor progress bars; verify all 25 reports generated
3. Verify concurrent execution is faster than sequential
4. Check no file write conflicts and thread pool stats displayed correctly

#### Test Scenario 3: Real-Time Dashboard
1. Select option 10; add new grades in another operation
2. Wait for auto-refresh (5 seconds) and verify stats update
3. Test pause/resume and manual refresh
4. Exit dashboard and verify background thread terminated

#### Test Scenario 4: Regex Validation
1. Try `"stu001"` → reject; try `"STU001"` → accept
2. Try `"john@uni"` → reject; try `"john@university.edu"` → accept
3. Try `"555-0123"` → reject; try all valid phone formats → accept
4. Verify all error messages show expected patterns

#### Test Scenario 5: Multi-Format File Operations
1. Export in all formats; verify CSV, JSON, and Binary files created
2. Import each format back; verify data integrity maintained

#### Test Scenario 6: Scheduled Tasks
1. Add daily GPA recalculation task; set execution ~2 minutes ahead
2. Wait and verify task runs automatically; check audit trail

#### Test Scenario 7: Pattern-Based Search
1. Search by `"@university.edu"` domain → verify only matching students shown
2. Try custom regex `"^[A-M].*"` → verify results
3. Try invalid regex → verify graceful error handling

#### Test Scenario 8: Stream Processing Performance
1. Create CSV with 10,000 grade records; import using streaming
2. Monitor memory; compare with full-load approach
3. Run parallel vs sequential stream statistics calculation; document speedup

#### Test Scenario 9: Thread Safety Verification
1. Start real-time dashboard; simultaneously add 50 grades and generate batch reports
2. Verify no `ConcurrentModificationException` or data corruption
3. Check audit trail shows all operations logged with no duplicates

#### Test Scenario 10: Unit Tests Execution
1. Run all JUnit tests: `mvn test`; verify all 25+ unit tests pass
2. Generate coverage report: `mvn jacoco:report`; verify 85%+ coverage
3. Review concurrency test results and document any failures

---
---

## Module 3.3: Task Management System

**Complexity:** Medium
**Time Estimate:** 6–8 hours
**Technology Stack:** Java 21 (LTS), IntelliJ IDEA Community Edition, JUnit 5

---

### Project Overview

In this lab, you will extend the Project/Task Management System from Week 2 by introducing advanced Java concepts — Collections, Functional Programming, File I/O (NIO), Regex, and Concurrency — to make the system more dynamic, expressive, persistent, and concurrent.

You will:
- Refactor Week 2's array-based logic into Collections (`ArrayList`, `HashMap`) for flexibility
- Integrate Functional Programming constructs (Lambdas, Streams, Functional Interfaces, Method References) to process and transform collection data more efficiently
- Add File I/O to persist projects and tasks
- Use Regex for input validation
- Implement basic concurrency to simulate simultaneous task updates

All data is stored in-memory during runtime but also saved and loaded from simple JSON-like text files. This lab prepares you for Week 4, where you'll transition from file storage to databases.

---

### Learning Objectives

By completing this lab, you will be able to:

- Refactor array-based logic to use Java Collections Framework (`List`, `Map`, `Set`)
- Implement functional programming with Lambdas, Functional Interfaces, and Method References
- Use the Streams API to perform filtering, mapping, and reduction operations on collections
- Implement file persistence with `java.nio.file.Files` and `Paths`
- Validate user inputs using regular expressions (`Pattern`, `Matcher`)
- Apply basic concurrency with `Thread`, `Runnable`, and `synchronized`
- Handle checked exceptions using try-with-resources for clean resource management
- Write and extend JUnit 5 tests for persistence, functional, and concurrent operations
- Maintain code quality through consistent naming, SOLID principles, and Git branching

---

### System Features Overview

#### Feature 1: Project Catalog with Collections and Streams
- Use `HashMap<String, Project>` to store and access projects
- Dynamically add/remove projects without array size limits
- Use Streams API to filter, sort, and aggregate project information
- Use Lambdas for concise iteration and data transformation

#### Feature 2: Task Management with Regex and Functional Validation
- Store tasks in `ArrayList<Task>` per project
- Enforce task ID pattern `T\d{3}` (e.g., T001)
- Validate all inputs using Regex before processing
- Implement `Predicate` or custom functional interfaces for filtering and validating task data

#### Feature 3: File Persistence (I/O with NIO)
- Save all projects and tasks to `projects_data.json` on exit
- Auto-load the file on startup using `Files.readAllLines()`
- Handle missing files and malformed data gracefully
- Use functional-style reading/writing with `Files.lines()` and stream processing

#### Feature 4: Concurrent and Functional Task Updates
- Simulate multi-user task updates with multiple threads
- Use `synchronized` methods to ensure thread safety
- Employ parallel streams or executor services for parallel updates
- Display progress as updates occur concurrently

#### Feature 5: Enhanced Testing & Git Integration
- Add JUnit tests for collection behaviors, Streams, file I/O, and threading
- Create Git branches for new features (e.g., `feature/file-io`)
- Commit with descriptive messages after major milestones

---

### Console UI Examples

#### Application Startup & File Load

```
╔════════════════════════════════════════════╗
║     JAVA PROJECT MANAGEMENT SYSTEM v3.0    ║
╚════════════════════════════════════════════╝
Loading projects from file...
✓ 5 projects loaded successfully from projects_data.json
```

#### Project Catalog (using HashMap and Streams)

```
──────────────────────────────────────────────────────────────
ID    | PROJECT NAME     | TYPE       | TASKS | COMPLETED (%)
──────────────────────────────────────────────────────────────
P001  | Alpha Tracker    | Software   |  5    |  80%
P002  | IoT Sensor Kit   | Hardware   |  3    |  50%
──────────────────────────────────────────────────────────────
```

Filter completed projects using Streams:
```java
projects.values().stream()
    .filter(p -> p.getCompletionRate() > 70)
    .forEach(System.out::println);
```

#### Adding Task with Regex and Functional Validation

```
Enter new task ID: TX01
❌ Error: Invalid Task ID format. Use pattern T### (e.g., T001)
Enter new task ID: T004
Enter task name: Write Unit Tests
✓ Task "Write Unit Tests" added successfully.
```

#### Saving Data to File

```
Saving project data...
Data written to projects_data.json successfully!
```

**Example `projects_data.json`:**
```json
[
  {
    "projectId": "P001",
    "name": "Alpha Tracker",
    "type": "Software",
    "tasks": [
      {"id": "T001", "name": "Design DB", "status": "Completed"},
      {"id": "T002", "name": "Implement API", "status": "In Progress"}
    ]
  },
  {
    "projectId": "P002",
    "name": "IoT Sensor Kit",
    "type": "Hardware",
    "tasks": [
      {"id": "T003", "name": "Build Prototype", "status": "Completed"}
    ]
  }
]
```

#### Concurrent Task Updates Example

```
╔════════════════════════════════════════════╗
║     PARALLEL TASK UPDATE SIMULATION        ║
╚════════════════════════════════════════════╝
Starting 3 threads...
Thread-1 updating T001 -> In Progress
Thread-2 updating T002 -> Completed
Thread-3 updating T003 -> Completed
All threads finished successfully.
✓ Task updates applied concurrently and safely.
```

#### JUnit Test Example

```java
@Test
void testFilterCompletedTasksUsingStreams() {
    List<Task> tasks = List.of(
        new Task("T001", "Design UI", "Completed"),
        new Task("T002", "Write Tests", "Pending")
    );
    long completed = tasks.stream()
        .filter(t -> t.getStatus().equals("Completed"))
        .count();
    assertEquals(1, completed);
}
```

#### File Error Handling

```
❌ Error: Unable to load projects_data.json (File not found)
→ Starting with empty catalog.
```

---

### Expected User Workflows

**Workflow 1: Startup and File Load**
System reads `projects_data.json` → displays number of projects loaded → proceeds to Main Menu.

**Workflow 2: Add Task with Regex and Functional Validation**
User inputs task ID → Regex ensures correct format (`T###`) → functional validation confirms uniqueness → task added on success.

**Workflow 3: Save and Exit**
User selects "Exit" → system serializes all data to file → confirms successful write.

**Workflow 4: Concurrent and Functional Task Update**
User triggers "Simulate Concurrent Updates" → threads or parallel streams update tasks → progress shown until all threads complete safely.

---

### User Stories

#### Epic 1: Project Management with Collections and Functional Programming

**US-1.1: Refactor Array Storage to Collections**
- Replace arrays with `ArrayList` and `HashMap`; use generics for type safety

**US-1.2: Stream-Based Search and Filtering**

> As a user, I want to quickly filter completed projects using Streams for efficient data processing.

**Technical Requirements:** Implement `filter()`, `map()`, and `collect()` operations with lambdas.

---

#### Epic 2: Regex Validation for Inputs

**US-2.1:** Validate Task IDs using regex `T\d{3}`; invalid formats throw `InvalidInputException`.

**US-2.2:** Validate Project IDs using regex `P\d{3}`; inform user if incorrect.

---

#### Epic 3: File Persistence

**US-3.1:** Save and Load Projects using `Files.writeString()` and `Files.readString()`; handle exceptions.

**US-3.2:** Auto-load on Startup and Save on Exit.

---

#### Epic 4: Concurrency & Thread Safety

**US-4.1:** Implement parallel task updates with `Runnable` threads or parallel streams.

**US-4.2:** Track completion and ensure thread safety with `synchronized` methods.

---

#### Epic 5: Testing & Git Integration

**US-5.1:** Add tests for Streams, file I/O, and threading.

**US-5.2:** Use Git feature branches and merge after validation.

---

### Project Structure

```
project-management-system/
│
├── src/
│   ├── Main.java
│   ├── models/
│   │   ├── Project.java
│   │   ├── SoftwareProject.java
│   │   ├── HardwareProject.java
│   │   ├── Task.java
│   │   ├── User.java
│   │   ├── RegularMember.java
│   │   ├── AdminMember.java
│   │   └── StatusReport.java
│   │
│   ├── interfaces/
│   │   ├── Completable.java
│   │   └── TaskFilter.java              # Functional interface for task filtering
│   │
│   ├── services/
│   │   ├── ProjectService.java
│   │   ├── TaskService.java
│   │   ├── ReportService.java
│   │   ├── ConcurrencyService.java
│   │   └── StreamService.java           # Stream and Lambda utilities
│   │
│   └── utils/
│       ├── ConsoleMenu.java
│       ├── ValidationUtils.java
│       ├── FileUtils.java
│       ├── RegexValidator.java
│       └── FunctionalUtils.java         # Functional helper methods
│
├── tests/
│   ├── ProjectTest.java
│   ├── TaskTest.java
│   ├── StreamOperationsTest.java
│   └── FilePersistenceTest.java
│
├── data/
│   └── projects_data.json
│
└── README.md
```

---

### Implementation Phases

#### Phase 1: Collections & Functional Refactor (2 hrs.)
- Refactor arrays to `ArrayList` and `HashMap`
- Introduce lambdas and Streams for filtering and mapping
- Ensure all existing tests pass

#### Phase 2: Add Regex Validation (1 hr.)
- Create `RegexValidator.java`
- Validate IDs using `Pattern` and `Matcher`

#### Phase 3: Implement File Persistence (2 hrs.)
- Add `FileUtils` with `saveProjects()` and `loadProjects()` using NIO and streams

#### Phase 4: Concurrency Integration (2–3 hrs.)
- Implement concurrent updates with threads or parallel streams
- Extend JUnit tests for new concurrent behavior

---

### Minimum Requirements Checklist

- [ ] JDK 21 and IntelliJ installed
- [ ] Arrays refactored to Collections (`ArrayList`, `HashMap`)
- [ ] Functional Programming (Lambdas, Streams, Functional Interfaces) implemented
- [ ] Regex validation implemented for IDs
- [ ] File persistence working (read & write)
- [ ] try-with-resources used for I/O
- [ ] Concurrent updates implemented with Threads or parallel streams
- [ ] JUnit tests cover stream and concurrency features
- [ ] Proper exception handling in all methods
- [ ] Git commits and feature branches used
- [ ] Clean, readable, SOLID code
- [ ] README updated

---

### Grading Rubric

| Criteria | Points | Excellent (90–100%) | Good (75–89%) | Satisfactory (60–74%) |
|---|---|---|---|---|
| Collections & Functional Refactor | 18 | Arrays replaced with Collections; Streams, Lambdas, and Functional Interfaces used effectively | Partial usage or inconsistent functional code | Minimal FP integration or misuse |
| File Persistence | 18 | Files saved/loaded via NIO; stream-based reads/writes; error handling clean | Works but lacks optimization | Inconsistent I/O or missing validation |
| Regex Validation | 12 | Robust ID validation with clear error messages | Works but partially applied | Weak or missing validation |
| Concurrency Implementation | 17 | Threads and parallel streams implemented; no race conditions | Threads run but minor sync issues | Limited concurrency demo |
| Testing & Git | 13 | Comprehensive JUnit and structured Git commits | Basic tests; some gaps | Few tests or unclear history |
| Code Quality & Docs | 10 | Modular, readable, fully documented | Minor clarity issues | Minimal documentation |
| Data Structures & Algorithms (DSA) | 10 | Efficient collection algorithms with functional logic | Logical structure, minor inefficiencies | Redundant logic |
| **Total** | **100** | | | |

---

### Submission Requirements

**Deliverables:**

Public GitHub repository with:
- Week 3 code (`src`, `tests`, `data`)
- `README.md` with setup steps and sample console output
- Screenshot of concurrent or stream-based operations
- Updated UML/Class diagram showing Streams integration
- JUnit test results screenshot

**Branch naming:** `feature/collections-fp`, `feature/file-io`, `feature/concurrency`

**Submission Link:** *(Insert submission form link here)*

---

### Testing the Application

#### Test Scenario 1: Load Projects from File
- Verify automatic loading from saved `.json` file

#### Test Scenario 2: Save Projects to File
- Confirm new data persists correctly after restart

#### Test Scenario 3: Add Project Using Collections
- Ensure dynamic list management and retrieval

#### Test Scenario 4: Validate IDs and Inputs with Regex
- Confirm proper format enforcement and error display

#### Test Scenario 5: Concurrency – Parallel Task Updates
- Run multi-threaded update simulation; verify data safety

#### Test Scenario 6: Exception Handling for File Operations
- Handle missing or malformed files gracefully

#### Test Scenario 7: Performance and Memory
- Add multiple projects and tasks; verify stability

#### Test Scenario 8: Functional Programming – Stream Operations
1. Use `filter()` to list completed tasks
2. Use `map()` to extract task names
3. Use `reduce()` to compute total completion
4. Confirm all results accurate

#### Test Scenario 9: Git Workflow and Versioning
- Ensure commits and merges reflect all FP and concurrency changes
