
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
