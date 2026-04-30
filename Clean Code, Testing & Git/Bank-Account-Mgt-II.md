
# Bank Account Management 

---

### Project Overview

Build a console-based Bank Account Management System that extends the Week 1 foundation. Users can create accounts, perform transactions (deposit, withdrawal, transfer), handle invalid inputs gracefully, and record all operations in memory using arrays.

This week focuses on:

- **Clean Code Practices** – refactoring, meaningful names, modular methods
- **Exception Handling** – using try-catch, throws, and custom exceptions
- **Testing Fundamentals** – applying JUnit for unit and integration tests
- **Version Control with Git** – creating branches, committing changes, and using git cherry-pick for code reuse

Future labs will enhance this version with Java Collections and file-based persistence.

---

### Learning Objectives

By completing this lab, you will be able to:

- Apply clean code principles for readability, maintainability, and scalability
- Implement robust exception handling to manage invalid inputs and transaction errors
- Write and execute unit tests with JUnit 5 for critical methods like `deposit()`, `withdraw()`, and `transfer()`
- Utilize Git for version control — initializing repositories, committing, branching, merging, and cherry-picking specific commits
- Refactor Week 1 classes (`Account`, `TransactionManager`, etc.) to improve structure and reduce redundancy
- Demonstrate code review and testing cycles to build confidence in software changes
- Prepare the codebase for Week 3 enhancements (Collections API and File Storage)

---

### System Features Overview

#### Feature 1: Refactored Account and Transaction Classes
- Simplify methods with clear names and comments
- Apply modular design to separate responsibilities (balance calculation vs. display)
- Introduce helper methods for common operations (e.g., `validateAmount()`)

#### Feature 2: Error Handling and Validation
- Handle invalid inputs with try-catch blocks
- Throw custom exceptions (e.g., `InsufficientFundsException`, `InvalidAccountException`)
- Ensure withdrawals don't exceed overdraft limits or go below minimum balance

#### Feature 3: Transaction Testing and Verification
- Write JUnit tests for `deposit()`, `withdraw()`, and `transfer()`
- Validate balance updates, exception conditions, and transaction records
- Log test results to console for clarity

#### Feature 4: Git Version Control Integration
- Initialize a Git repository and track code changes
- Use branches for features (e.g., `feature/error-handling`, `feature/testing`)
- Merge and cherry-pick commits across branches for controlled integration

#### Feature 5: Enhanced Console User Experience
- Display error messages clearly
- Add confirmation prompts for transactions
- Simulate test outputs in the console (UI and JUnit summary)

---

### Console UI Examples

#### 1. Main Menu (Refactored)

```
╔════════════════════════════════════════════╗
║      BANK ACCOUNT MANAGEMENT SYSTEM        ║
╚════════════════════════════════════════════╝

Main Menu:
-----------
1. Manage Accounts
2. Perform Transactions
3. Generate Account Statements
4. Run Tests
5. Exit

Enter your choice: _
```

#### 2. Error Handling Example – Invalid Deposit

```
Enter Account Number: ACC999
❌ Error: Account not found. Please check the account number and try again.

Enter Account Number: ACC001
Enter amount to deposit: -200
❌ Error: Invalid amount. Amount must be greater than 0.
```

#### 3. Transaction Failure Example – Insufficient Funds

```
PROCESS TRANSACTION
─────────────────────────────────────────────
Enter Account Number: ACC002
Select type: 2 (Withdrawal)
Enter amount: $10,000
❌ Transaction Failed: Insufficient funds. Current balance: $2,950.00
```

#### 4. JUnit Test Output Example

```
Running tests with JUnit...

Test: depositUpdatesBalance() .......... PASSED
Test: withdrawBelowMinimumThrowsException() .......... PASSED
Test: overdraftWithinLimitAllowed() .......... PASSED
Test: overdraftExceedThrowsException() .......... PASSED

✓ All 4 tests passed successfully!
```

#### 5. Git Workflow Example

```
> git init
> git add .
> git commit -m "Initial refactoring for clean code"
> git branch feature/testing
> git checkout feature/testing
> git commit -m "Add JUnit tests for transactions"
> git checkout main
> git cherry-pick <commit-hash-of-tests>
> git push origin main
✓ Cherry-picked JUnit test changes successfully!
```

#### 6. Statement Generation Example (with Error Handling)

```
GENERATE ACCOUNT STATEMENT
─────────────────────────────────────────────
Enter Account Number: ACC001

Account: John Smith (Savings)
Current Balance: $6,750.00

Transactions:
────────────────────────────────────────────────────
TXN001 | DEPOSIT    | +$1,500.00 | $6,750.00
TXN002 | WITHDRAWAL | -$750.00   | $5,250.00
────────────────────────────────────────────────────
Net Change: +$750.00

✓ Statement generated successfully.
```

#### 7. Application Exit

```
Thank you for using the Bank Account Management System!
All data saved in memory. Remember to commit your latest changes to Git!
Goodbye!
```

---

### Expected User Workflows

#### Workflow 1: Handle Transaction Error
1. User selects "Perform Transactions"
2. Enters invalid account number → error message displayed
3. Re-enters valid account number
4. Attempts withdrawal beyond balance → custom exception shown
5. Performs valid withdrawal → success confirmed

#### Workflow 2: Run JUnit Tests
1. User selects "Run Tests"
2. System executes unit tests on core methods
3. Results display as Passed/Failed
4. User reviews Git commit to store test results

#### Workflow 3: Version Control Integration
1. Developer creates `feature/error-handling` branch
2. Implements exceptions and tests
3. Commits and pushes to branch
4. Merges into main using `git merge`
5. Uses `git cherry-pick` to bring selected fix commits into testing branch

#### Workflow 4: Statement Generation with Refactored Code
1. User selects "Generate Statement"
2. System fetches transactions from array
3. Applies error handling for empty records
4. Generates summary with totals and balances

---

### User Stories

#### Epic 1: Error Handling and Validation

**US-1.1: Handle Invalid Deposits**

> As a user, I want to see clear errors for negative deposit amounts so that I don't crash the program.

**Acceptance Criteria:** Negative amounts throw `InvalidAmountException`.

**US-1.2: Prevent Overdraft Exceeding Limit**

**Acceptance Criteria:** Withdrawals beyond limit trigger `OverdraftExceededException`.

**Technical Requirements:**
- Use try-catch for input validation
- Define custom exception classes for specific errors

---

#### Epic 2: Code Refactoring and Clean Design

**US-2.1: Refactor TransactionManager for Readability**
- Break long methods into smaller modular ones (e.g., `validateTransaction`, `applyTransaction`)
- Rename variables for clarity

**US-2.2: Apply Comments and Formatting Standards**
- Follow Google Java Style Guide for naming and indentation

**Technical Requirements:**
- Run manual review to ensure methods ≤ 25 lines
- Add JavaDoc comments to each public method

---

#### Epic 3: Testing and Verification

**US-3.1: Write Unit Tests for Deposit and Withdraw**

**Acceptance Criteria:** Tests pass for valid and invalid cases.

**US-3.2: Test Transfer Between Accounts**
- Check balance updates in both accounts

**Technical Requirements:**
- Use JUnit 5
- Organize tests under `src/test/java`
- Apply `@BeforeEach` to reset test data

---

#### Epic 4: Git Version Control Workflows

**US-4.1: Implement Feature Branching**
- Create and switch branches using `git branch` and `git checkout`

**US-4.2: Cherry-Pick Specific Commits**
- Selectively apply tested commits across branches

**Technical Requirements:**
- Include Git commands in README
- Perform at least 3 commits during lab progression

---

#### Epic 5: Statement Generation Enhancement

**US-5.1: Generate Error-Free Statements**
- Handle accounts with no transactions gracefully
- Format output for clarity and totals

**Technical Requirements:**
- Sort transactions by timestamp (newest first)
- Ensure balance summaries use 2-decimal precision

---

### Project Structure

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
│   │   ├── Transaction.java
│   │   ├── exceptions/
│   │   │   ├── InvalidAmountException.java
│   │   │   ├── InsufficientFundsException.java
│   │   │   └── OverdraftExceededException.java
│   │
│   ├── services/
│   │   ├── AccountManager.java
│   │   ├── TransactionManager.java
│   │   └── StatementGenerator.java
│   │
│   └── utils/
│       └── ValidationUtils.java
│
├── src/test/java/
│   ├── AccountTest.java
│   ├── TransactionManagerTest.java
│   └── ExceptionTest.java
│
├── docs/
│   └── git-workflow.md
│
└── README.md
```

---

### Implementation Phases

#### Phase 1: Setup and Refactoring (1–2 hours)

**Tasks:**
- Fork Week 1 repo and create a new repo for Week 2, then create a new branch `feature/refactor`
- Refactor `Account` and `TransactionManager` for clarity
- Add JavaDocs and consistent naming

**Git Commands:**
```bash
git checkout -b feature/refactor
git add .
git commit -m "Refactored AccountManager and TransactionManager"
```

#### Phase 2: Exception Handling

**Tasks:**
- Create custom exceptions
- Wrap input validation in try-catch blocks
- Update UI to display errors gracefully

**Git Commands:**
```bash
git checkout -b feature/exceptions
git commit -m "Commit Message"
```

#### Phase 3: Testing and Verification (2 hours)

**Tasks:**
- Add JUnit 5 to project
- Write unit tests for deposit, withdraw, transfer
- Run and document results

**Git Commands:**
```bash
git checkout -b feature/testing
git add <file-to-be-added>
git commit -m "Commit Message"
git cherry-pick <refactor-commit-hash>
```

#### Phase 4: Merge and Documentation

**Tasks:**
- Merge branches and resolve conflicts
- Document Git workflow in README
- Submit final repository

---

### Minimum Requirements Checklist

- [ ] All custom exceptions implemented
- [ ] JUnit tests created and passing
- [ ] Code refactored for clean structure
- [ ] Git repository initialized with branching and cherry-pick usage
- [ ] README includes Git workflow and test results
- [ ] All Week 1 features are still functional

---

### Grading Rubric

| Criteria | Points | Excellent (90–100%) | Good (75–89%) | Satisfactory (60–74%) |
|---|---|---|---|---|
| Clean Code & Refactoring | 20 | Consistent naming, JavaDocs, DRY methods | Mostly refactored, minor redundancy | Basic clean-up applied |
| Exception Handling | 20 | Custom exceptions, robust try-catch | Handled core cases | Limited validation |
| Testing & Verification (JUnit) | 20 | Comprehensive unit tests, edge cases covered | Core tests only | Minimal testing |
| Git Version Control | 15 | Branches, merges, and cherry-picks used effectively | Basic branch workflow | Single branch |
| Functionality & Stability | 15 | All Week 1 features enhanced and stable | Minor bugs | Partially functional |
| DSA (Use of Arrays & Algorithms) | 10 | Efficient array management and search/sort logic | Functional but not optimized | Inefficient iteration |
| Documentation | 10 | Clear README + Git docs included | Partial docs | Limited notes |
| **Total** | **100** | | | |

---

### Testing the Application

#### Test Scenario 1: Refactored Account Creation
1. Run the refactored application
2. Select option 1 (Create Account)
3. Enter valid details for a Savings Account (Regular Customer)
4. Verify constructors and encapsulation work correctly (no direct field access)
5. Confirm auto-generated Account ID (e.g., ACC001)
6. Check console output for clean, formatted messages and no redundant lines

#### Test Scenario 2: Deposit Operation with Exception Handling
1. Select option 2 (Perform Transactions)
2. Enter invalid account number (e.g., ACC999)
3. Verify custom exception (`InvalidAccountException`) displays a user-friendly message
4. Enter valid account number and positive deposit amount
5. Confirm balance updates correctly and transaction logs are recorded

#### Test Scenario 3: Withdrawal and Overdraft Validation
1. Select option 2 (Perform Transactions)
2. Choose Withdrawal on a Checking Account
3. Enter an amount exceeding balance but within overdraft limit → should succeed
4. Enter amount beyond overdraft limit → should throw `OverdraftExceededException`
5. Confirm final balance accuracy and transaction count increment

#### Test Scenario 4: Statement Generation After Refactoring
1. Select option 3 (Generate Account Statement)
2. Enter valid account number
3. Verify clean, formatted output using refactored methods
4. Confirm transactions display in reverse chronological order
5. Ensure summary totals (deposits, withdrawals, net change) are correct

#### Test Scenario 5: Exception Handling for Invalid Inputs
1. At main menu, enter invalid choice (e.g., letters instead of numbers)
2. Attempt deposit with negative amount or zero
3. Verify custom exceptions (`InvalidAmountException`, `InputMismatchException`) are caught
4. Check program continues running without crashing
5. Confirm retry prompts appear correctly

#### Test Scenario 6: Run JUnit Tests
1. Open JUnit test classes (`AccountTest`, `TransactionManagerTest`, `ExceptionTest`)
2. Run unit tests for deposit, withdraw, and transfer methods
3. Verify all assertions pass (expected vs actual balances)
4. Confirm exception-based tests (`assertThrows`) behave as intended
5. Check JUnit summary shows all tests successful

#### Test Scenario 7: Git Cherry-Pick, Push, and Code Quality Verification
1. Switch to branch `feature/error-handling` and use `git cherry-pick <commit-hash>` to apply selected tested commits
2. Resolve conflicts if any; verify the app compiles and runs correctly
3. Push final code to remote (`git push origin main`) and confirm commits and branches appear on GitHub
4. Check `.gitignore`, `README.md`, and code formatting for consistency
5. Ensure JavaDocs, clean indentation, and meaningful commit messages are present

---

### Submission Requirements

**Deliverables:**

Public GitHub repository with:
- Source code (`/src`)
- JUnit tests (`/src/test/java`)
- Git workflow documentation (`/docs/git-workflow.md`)
- README with setup, testing, and branching instructions
- At least 5 Git commits showing progress (refactor, exceptions, testing, merge)

**Submission Link:** *(Insert Google Form or LMS link here)*

---
---

## Module 2.1: Student Grade Management System

**Complexity:** Medium
**Time Estimate:** 6–7 hours

---

### Objectives

By completing this project, you will be able to:

- Create robust, production-ready Java applications that implement comprehensive exception handling strategies, unit tests with JUnit and Mockito, and follow SOLID principles for maintainability
- Apply Git workflows and branching strategies to collaborate effectively on team projects, managing feature development, code integration, and version history with proper commit practices
- Evaluate code quality by analyzing adherence to clean code principles, assessing test coverage adequacy, and using static analysis tools to identify areas for improvement
- Analyze complex bugs using IDE debugging tools combined with systematic testing approaches to identify root causes and implement appropriate fixes
- Create comprehensive test suites that effectively isolate dependencies through mocking, validate business logic through unit tests, and can be integrated into automated build and CI/CD pipelines

---

### What You'll Build

An enhanced Student Grade Management System with:

#### New Features (Building on Lab 1)
- **Export Grade Report** – Save student reports to text files
- **Calculate GPA** – Convert percentage grades to 4.0 GPA scale
- **Bulk Grade Import** – Load multiple grades from CSV file
- **Grade Statistics** – View class-wide analytics (highest, lowest, median, standard deviation)
- **Student Search** – Find students by name or ID with partial matching

#### Quality Improvements
- **Exception Handling** – Custom exceptions for all error scenarios
- **Unit Tests** – Comprehensive JUnit tests with 80%+ coverage
- **SOLID Principles** – Refactored code following SOLID
- **Git Workflow** – Feature branch workflow with proper commits
- **Input Validation** – Robust validation with helpful error messages
- **Logging** – Application-wide logging for debugging

---

### Console Output Examples

#### Screenshot 1: Enhanced Main Menu

```
╔════════════════════════════════════════════╗
║   STUDENT GRADE MANAGEMENT - MAIN MENU     ║
╚════════════════════════════════════════════╝

1. Add Student
2. View Students
3. Record Grade
4. View Grade Report
5. Export Grade Report          [NEW]
6. Calculate Student GPA        [NEW]
7. Bulk Import Grades           [NEW]
8. View Class Statistics        [NEW]
9. Search Students              [NEW]
10. Exit

Enter choice: _
```

#### Screenshot 2: Export Grade Report

```
Enter choice: 5

EXPORT GRADE REPORT
─────────────────────────────────────────────

Enter Student ID: STU001

Student: STU001 - Alice Johnson
Type: Regular Student
Total Grades: 5

Export options:
1. Summary Report (overview only)
2. Detailed Report (all grades)
3. Both

Select option (1-3): 2

Enter filename (without extension): alice_johnson_report

✓ Report exported successfully!
  File: alice_johnson_report.txt
  Location: ./reports/
  Size: 2.4 KB
  Contains: 5 grades, averages, performance summary

Press Enter to continue...
```

#### Screenshot 3: Calculate Student GPA

```
Enter choice: 6

CALCULATE STUDENT GPA
─────────────────────────────────────────────

Enter Student ID: STU002

Student: STU002 - Bob Smith
Type: Honors Student
Overall Average: 87.4%

GPA CALCULATION (4.0 Scale)
─────────────────────────────────────────────
Subject          | Grade  | GPA Points
─────────────────────────────────────────────
Mathematics      | 92%    | 4.0 (A)
English          | 85%    | 3.7 (A-)
Science          | 88%    | 3.7 (A-)
Music            | 91%    | 4.0 (A)
Art              | 81%    | 3.3 (B+)
─────────────────────────────────────────────

Cumulative GPA: 3.74 / 4.0
Letter Grade: A-
Class Rank: 2 of 5

Performance Analysis:
✓ Excellent performance (3.5+ GPA)
✓ Honors eligibility maintained
✓ Above class average (3.12 GPA)

Press Enter to continue...
```

#### Screenshot 4: Bulk Import Grades

```
Enter choice: 7

BULK IMPORT GRADES
─────────────────────────────────────────────

Place your CSV file in: ./imports/

CSV Format Required:
StudentID,SubjectName,SubjectType,Grade
Example: STU001,Mathematics,Core,85

Enter filename (without extension): october_grades

Validating file... ✓
Processing grades...

IMPORT SUMMARY
─────────────────────────────────────────────
Total Rows: 15
Successfully Imported: 13
Failed: 2

Failed Records:
Row 7: Invalid student ID (STU999)
Row 12: Grade out of range (105)

✓ Import completed!
  13 grades added to system
  See import_log_20251103.txt for details

Press Enter to continue...
```

#### Screenshot 5: View Class Statistics

```
Enter choice: 8

CLASS STATISTICS
─────────────────────────────────────────────

Total Students: 5
Total Grades Recorded: 47

GRADE DISTRIBUTION
─────────────────────────────────────────────
90-100% (A):  ████████████████░░░░  42.6% (20 grades)
80-89%  (B):  ██████████████░░░░░░  36.2% (17 grades)
70-79%  (C):  ██████░░░░░░░░░░░░░░  14.9% (7 grades)
60-69%  (D):  ██░░░░░░░░░░░░░░░░░░  4.3%  (2 grades)
0-59%   (F):  █░░░░░░░░░░░░░░░░░░░  2.1%  (1 grade)

STATISTICAL ANALYSIS
─────────────────────────────────────────────
Mean (Average):      81.4%
Median:              83.0%
Mode:                85.0%
Standard Deviation:  10.2%
Range:               58.0% (42% - 100%)

Highest Grade:       100% (STU004 - Science)
Lowest Grade:        42% (STU003 - Mathematics)

SUBJECT PERFORMANCE
─────────────────────────────────────────────
Core Subjects:       83.2% average
  Mathematics:       79.5%
  English:           84.1%
  Science:           86.0%

Elective Subjects:   78.9% average
  Music:             82.3%
  Art:               77.8%
  Physical Ed:       76.5%

STUDENT TYPE COMPARISON
─────────────────────────────────────────────
Regular Students:    75.8% average (3 students)
Honors Students:     89.1% average (2 students)

Press Enter to continue...
```

#### Screenshot 6: Search Students

```
Enter choice: 9

SEARCH STUDENTS
─────────────────────────────────────────────

Search options:
1. By Student ID
2. By Name (partial match)
3. By Grade Range
4. By Student Type

Select option (1-4): 2

Enter name (partial or full): John

SEARCH RESULTS (2 found)
─────────────────────────────────────────────
STU ID   | NAME              | TYPE         | AVG
─────────────────────────────────────────────
STU001   | Alice Johnson     | Regular      | 81.2%
STU002   | Bob Johnson       | Honors       | 87.4%
─────────────────────────────────────────────

Actions:
1. View full details for a student
2. Export search results
3. New search
4. Return to main menu

Enter choice: _
```

#### Screenshot 7: Exception Handling Example

```
Enter choice: 3

RECORD GRADE
─────────────────────────────────────────────

Enter Student ID: STU999

✗ ERROR: StudentNotFoundException
  Student with ID 'STU999' not found in the system.

  Available student IDs: STU001, STU002, STU003, STU004, STU005

  Try again? (Y/N): Y

Enter Student ID: STU001

Student Details:
Name: Alice Johnson
Type: Regular Student
Current Average: 81.2%

...

Enter grade (0-100): 150

✗ ERROR: InvalidGradeException
  Grade must be between 0 and 100.
  You entered: 150

  Try again? (Y/N): Y

Enter grade (0-100): 95

✓ Grade recorded successfully!
```

---

### User Stories

#### US-1: Enhanced Exception Handling (NEW)

> **As a** developer
> **I want to** handle all errors gracefully
> **So that** the application never crashes unexpectedly

**Acceptance Criteria:**
- Custom exceptions for all error scenarios
- Informative error messages with recovery suggestions
- No use of generic `Exception` catching
- All exceptions logged with timestamps
- Input validation prevents most exceptions before they occur

#### US-2: Export Grade Report (NEW)

> **As a** teacher
> **I want to** export grade reports to files
> **So that** I can share them with students and parents

**Acceptance Criteria:**
- Export summary or detailed reports
- Save to text files in `reports/` directory
- Include student info, all grades, averages, and performance analysis
- Handle file I/O exceptions properly
- Confirm export success with file location and size

#### US-3: Calculate Student GPA (NEW)

> **As a** teacher
> **I want to** calculate GPA on a 4.0 scale
> **So that** I can provide standardized grade reporting

**Acceptance Criteria:**
- Convert percentage grades to 4.0 GPA scale
- Display grade breakdown by subject
- Show letter grades (A, A-, B+, etc.)
- Calculate cumulative GPA
- Display class rank

**Grading Scale:**

| Percentage | GPA | Letter |
|---|---|---|
| 93–100% | 4.0 | A |
| 90–92% | 3.7 | A- |
| 87–89% | 3.3 | B+ |
| 83–86% | 3.0 | B |
| 80–82% | 2.7 | B- |
| 77–79% | 2.3 | C+ |
| 73–76% | 2.0 | C |
| 70–72% | 1.7 | C- |
| 67–69% | 1.3 | D+ |
| 60–66% | 1.0 | D |
| Below 60% | 0.0 | F |

#### US-4: Bulk Import Grades (NEW)

> **As a** teacher
> **I want to** import multiple grades from a CSV file
> **So that** I can efficiently enter grades for the whole class

**Acceptance Criteria:**
- Read CSV files from `imports/` directory
- Validate file format before processing
- Validate each row (student exists, grade in range, subject valid)
- Skip invalid rows but continue processing
- Generate import summary with success/failure counts
- Create detailed log file of import process

**CSV Format:**
```
StudentID,SubjectName,SubjectType,Grade
STU001,Mathematics,Core,85
STU002,English,Core,92
STU001,Music,Elective,78
```

#### US-5: View Class Statistics (NEW)

> **As a** teacher
> **I want to** view class-wide statistics
> **So that** I can understand overall class performance

**Acceptance Criteria:**
- Display grade distribution (A, B, C, D, F counts and percentages)
- Show statistical measures (mean, median, mode, standard deviation)
- Display highest and lowest grades with student names
- Show average performance by subject
- Compare Regular vs Honors student performance

#### US-6: Search Students (NEW)

> **As a** teacher
> **I want to** search for students
> **So that** I can quickly find specific students or groups

**Acceptance Criteria:**
- Search by student ID (exact match)
- Search by name (partial match, case-insensitive)
- Search by grade range (e.g., 80–90%)
- Search by student type (Regular/Honors)
- Display search results in a table
- Allow actions on search results (view details, export)

---

### New Architecture Requirements

#### SOLID Principles Implementation

**Single Responsibility Principle (SRP)**
- `ReportGenerator`: Only generates reports
- `FileExporter`: Only handles file operations
- `GPACalculator`: Only performs GPA calculations
- `StatisticsCalculator`: Only performs statistical calculations
- `CSVParser`: Only parses CSV files

**Open/Closed Principle (OCP)**
- Subject hierarchy can be extended with new subject types without modifying existing code
- Student hierarchy can be extended with new student types
- Strategy pattern for grade calculation (can add different grading scales)

**Liskov Substitution Principle (LSP)**
- Any `Student` subclass can be used wherever `Student` is expected
- Any `Subject` subclass can be used wherever `Subject` is expected

**Interface Segregation Principle (ISP)**
- Create focused interfaces: `Searchable`, `Exportable`, `Calculable`
- Clients only depend on methods they use

**Dependency Inversion Principle (DIP)**
- High-level modules (`BulkImportService`) depend on abstractions (`CSVParser` interface)
- Use dependency injection in service classes

---

### Testing Requirements

#### JUnit Tests (80%+ Coverage Required)

**Test Coverage Goals:**

| Scope | Target |
|---|---|
| Overall | 80%+ |
| Critical business logic (GPA calculation, statistics) | 95%+ |
| Exception handling paths | 100% |
| Service classes | 85%+ |

---

### Git Workflow Requirements

#### Branch Strategy

| Branch | Purpose |
|---|---|
| `main` | Production-ready code (protected) |
| `develop` | Integration branch |
| `feature/*` | Feature branches (e.g., `feature/export-reports`) |
| `bugfix/*` | Bug fix branches |
| `hotfix/*` | Emergency fixes |

#### Commit Requirements

Minimum 20 meaningful commits following conventional commit format:

```
feat: add GPA calculation feature
fix: correct median calculation for even count
test: add unit tests for StatisticsCalculator
refactor: extract file operations to FileExporter
docs: update README with testing instructions
```

#### Required Git Workflow
1. Create feature branch from `develop`
2. Implement feature with regular commits
3. Write tests for the feature
4. Merge `develop` into feature branch (resolve conflicts if any)
5. Create pull request with description
6. Merge to `develop`
7. Eventually merge `develop` to `main`

---

### Minimum Requirements

**Implementation**
- [ ] All custom exceptions implemented
- [ ] All 6 new user stories working
- [ ] SOLID principles applied throughout
- [ ] Exception handling on all user inputs and file operations
- [ ] Logging implemented for debugging
- [ ] All service classes use dependency injection

**Testing**
- [ ] JUnit and Mockito dependencies added (Maven/Gradle)
- [ ] Minimum 15 unit tests
- [ ] Minimum 5 integration tests with mocking
- [ ] 80%+ code coverage achieved
- [ ] All tests pass
- [ ] Test reports generated

**Git**
- [ ] Feature branch workflow followed
- [ ] Minimum 20 meaningful commits
- [ ] Conventional commit messages
- [ ] `.gitignore` properly configured
- [ ] `CHANGELOG.md` maintained
- [ ] Pull requests documented (screenshots/descriptions)

**Code Quality**
- [ ] No code duplication
- [ ] Single Responsibility Principle followed
- [ ] Proper dependency injection
- [ ] Consistent naming conventions
- [ ] Comprehensive JavaDoc comments
- [ ] No hardcoded values (use constants)

**Documentation**
- [ ] README with setup and testing instructions
- [ ] CHANGELOG documenting all features
- [ ] JavaDoc for all public methods
- [ ] Test execution guide
- [ ] Git workflow documentation

---

### Grading Rubric

| Criteria | Points | What We're Looking For |
|---|---|---|
| Exception Handling | 15 | All custom exceptions implemented, proper error handling, informative messages, no generic catches |
| Testing (JUnit/Mockito) | 20 | 80%+ coverage, meaningful tests, proper mocking, tests pass, integration tests included |
| SOLID Principles | 15 | SRP evident, OCP in hierarchies, LSP maintained, ISP with focused interfaces, DIP with injection |
| Git Workflow | 15 | Feature branches, 20+ commits, conventional messages, pull requests, proper branching strategy |
| New Functionality | 20 | All 6 user stories work correctly: export reports, GPA calculation, bulk import, statistics, search |
| Code Quality | 10 | Clean code, no duplication, proper naming, JavaDoc comments, constants used |
| Documentation | 5 | README, CHANGELOG, test instructions, Git workflow docs |
| **Total** | **100** | |

---

### Testing the Application

#### Test Scenario 1: Exception Handling
1. Try to record grade for non-existent student → verify `StudentNotFoundException` is thrown and caught
2. Try to enter grade > 100 → verify `InvalidGradeException` is thrown and caught
3. Try to import CSV with invalid format → verify `InvalidFileFormatException` is thrown

#### Test Scenario 2: Export Grade Report
1. Add student and record 5+ grades
2. Select option 5 (Export Grade Report)
3. Enter student ID, select detailed report, provide filename
4. Verify file is created in `reports/` directory
5. Open file and verify content is correct

#### Test Scenario 3: Calculate GPA
1. Select option 6 (Calculate Student GPA)
2. Enter student ID with multiple grades
3. Verify GPA calculation is correct
4. Verify letter grades match percentages
5. Verify class rank is displayed
6. Test with different grade ranges (A, B, C, etc.)

#### Test Scenario 4: Bulk Import
1. Create CSV file with 10 valid records and 2 invalid records (invalid student ID, grade > 100)
2. Place file in `imports/` directory
3. Select option 7 (Bulk Import Grades) and enter filename
4. Verify 10 succeed, 2 fail
5. Check import log file is created
6. Verify grades appear in system

#### Test Scenario 5: Class Statistics
1. Ensure at least 5 students with 5+ grades each
2. Select option 8 (View Class Statistics)
3. Verify grade distribution, mean, median, mode calculations
4. Verify highest/lowest grades shown correctly
5. Verify subject averages are correct

#### Test Scenario 6: Search Students
1. Select option 9 (Search Students)
2. Search by name with partial match ("John") → verify all matching students appear
3. Search by grade range (80–90%) → verify only students in range appear
4. Search by student type (Honors) → verify only honors students appear

#### Test Scenario 7: Unit Tests
1. Run all JUnit tests: `mvn test` or IDE test runner
2. Verify all tests pass
3. Generate coverage report → verify 80%+ coverage achieved

#### Test Scenario 8: Git Workflow
1. Review commit history: `git log --oneline` → verify 20+ commits
2. Verify conventional commit messages
3. Check branch structure: `git branch -a` → verify feature branches exist
4. Review `CHANGELOG.md` for documented changes

**Submission Link:** Submit your project here: [Tally](#)

---
---

## Module 2.3: Task Management System

**Complexity:** Medium
**Time Estimate:** 6–8 hours
**Technology Stack:** Java 21 (LTS), IntelliJ IDEA Community Edition, JUnit 5

---

### Project Overview

This lab builds on Lab 1 – Java Basics by refactoring the Project/Task Management System for cleaner, safer, and testable code. You'll apply exception handling, SOLID principles, and unit testing using JUnit 5, while maintaining version control with Git.

All functionality from Lab 1 (Project creation, Task management, Completion averages) remains, but now enhanced with:

- Custom exceptions for invalid inputs
- Refactored, modular code with better naming and organization
- Basic JUnit tests for core functions
- Git repository setup and proper commit workflow

All data remains in memory using arrays (no external DB). Future labs will introduce collections and file persistence.

---

### Learning Objectives

By completing this lab, you will be able to:

- Apply clean code principles (SOLID, naming conventions, method modularity)
- Implement exception handling using try-catch blocks and custom exceptions
- Refactor Lab 1 code for improved readability and maintainability
- Write and run JUnit unit tests for methods like task status updates and completion calculations
- Use Git for source control: initialize repositories, commit changes, create branches, and merge
- Evaluate code quality through consistent indentation, comments, and naming
- Handle invalid user inputs gracefully through custom exception messages
- Prepare the system for future enhancements (Week 3 will replace arrays with collections)

---

### System Features Overview

#### Feature 1: Project Catalog Management
- Same as Lab 1 (creating and listing projects)
- Add validation via custom exceptions (e.g., `InvalidProjectDataException`)
- Enforce unique project IDs and positive budgets

#### Feature 2: Task Operations
- Handle invalid task assignments gracefully (throw `TaskNotFoundException`)
- Refactor task creation/update methods for clarity
- Add unit tests for task status updates and progress calculation

#### Feature 3: User Management
- Refactor user logic to separate responsibilities (e.g., `UserService`)
- Validate email and role inputs through exceptions
- Use Git branches for adding new user roles (clean commit history)

#### Feature 4: Status Processing & Reporting
- Add validation for projects with no tasks (throw `EmptyProjectException`)
- Test average calculation methods via JUnit
- Refactor printing logic to utility methods

#### Feature 5: Menu Navigation & User Experience
- Improve input validation with exception handling
- Display user-friendly error messages for invalid entries
- Ensure menu loops remain stable under exceptions

---

### Console UI Examples

#### 1. Main Menu

```
╔════════════════════════════════════════════╗
║     JAVA PROJECT MANAGEMENT SYSTEM         ║
╚════════════════════════════════════════════╝

Current User: Alice Johnson (Admin)

Main Menu:
-----------
1. Manage Projects
2. Manage Tasks
3. View Status Reports
4. Switch User
5. Exit

Enter your choice: _
```

#### 2. Invalid Input Handled via Exception

```
Enter project ID: P999
❌ Error: ProjectNotFoundException – Project ID 'P999' does not exist.
Please try again.

Enter project ID: P001
✓ Project 'Alpha Tracker' loaded successfully.
```

#### 3. Add Task – Validation

```
╔════════════════════════════════════════════╗
║               ADD NEW TASK                 ║
╚════════════════════════════════════════════╝

Enter task name: Implement API
Enter status (Pending/In Progress/Completed): In Progress

✓ Task 'Implement API' successfully added to Project P001.
```

#### 4. Exception During Task Update

```
Enter task ID: T999
❌ Error: TaskNotFoundException – Task 'T999' was not found in the project.

Operation aborted. Returning to task menu...
```

#### 5. Status Report Display

```
╔════════════════════════════════════════════╗
║            PROJECT STATUS REPORT           ║
╚════════════════════════════════════════════╝

PROJECT ID | PROJECT NAME      | TASKS | COMPLETED | PROGRESS (%)
-----------------------------------------------------------------
P001       | Alpha Tracker     |   4   |    3      |   75%
P002       | IoT Sensor Kit    |   2   |    1      |   50%
-----------------------------------------------------------------
AVERAGE COMPLETION: 62.5%

✓ Report generated successfully.
```

#### 6. Git Commit Workflow

```bash
$ git init
$ git add .
$ git commit -m "Refactor: Added custom exceptions and cleaned class structure"
$ git branch feature/testing
$ git checkout feature/testing
$ git add src/test
$ git commit -m "Test: Added JUnit test for progress calculation"
$ git checkout main
$ git merge feature/testing
```

#### 7. JUnit Test Example

```java
@Test
void testCalculateCompletionPercentage() {
    Project p = new SoftwareProject("P001", "Alpha Tracker", 5, 15000);
    p.addTask(new Task("T001", "Setup DB", "Completed"));
    p.addTask(new Task("T002", "Design UI", "In Progress"));

    double result = p.calculateCompletionPercentage();
    assertEquals(50.0, result);
}
```

---

### Expected User Workflows

**Workflow 1: Refactor and Run**
User opens existing Lab 1 project → Refactors code → Runs updated program → Confirms all previous features still work.

**Workflow 2: Exception Handling**
User enters invalid data (e.g., negative budget) → System throws custom exception → Displays error → Returns to menu without crashing.

**Workflow 3: Unit Testing**
User writes JUnit tests for `calculateCompletionPercentage()` → Runs tests → All pass with green indicators.

**Workflow 4: Git Versioning**
User initializes Git repo → Makes commits after refactoring and testing → Creates branch for new exceptions → Merges cleanly.

---

### User Stories

#### Epic 1: Code Refactoring

**US-1.1: Refactor Class Design**

> As a developer, I want to simplify methods and names so that the code is easier to maintain.

**Acceptance Criteria:**
- No duplicate logic
- Descriptive method and variable names
- Single Responsibility per class

**Technical Requirements:**
- Apply SOLID principles (Single Responsibility, Open/Closed)
- Split large methods into smaller ones
- Use meaningful naming and comments

---

#### Epic 2: Exception Handling

**US-2.1: Handle Invalid Inputs**

> As a system, I want to catch invalid user inputs so that the program does not crash.

**Acceptance Criteria:**
- Throws custom exceptions (e.g., `InvalidInputException`, `TaskNotFoundException`)
- Displays clear error messages
- Logs errors to console gracefully

**Technical Requirements:**
- Use try-catch-finally blocks
- Create custom exception classes in `utils.exceptions`
- Handle validation centrally via `ValidationUtils`

---

#### Epic 3: Testing Fundamentals

**US-3.1: Test Completion Calculation**

> As a developer, I want to verify that completion percentages are accurate.

**Acceptance Criteria:**
- At least 3 JUnit tests for different cases (no tasks, partial, all completed)
- All tests pass successfully

**Technical Requirements:**
- Add `src/test/java/` directory
- Use JUnit 5 annotations (`@Test`, `@BeforeEach`)
- Assertions: `assertEquals`, `assertThrows`

---

#### Epic 4: Git Version Control

**US-4.1: Version Code Changes**

> As a developer, I want to track changes and refactors using Git so that my code history is maintained.

**Acceptance Criteria:**
- Repository initialized and linked to GitHub
- Minimum 3 meaningful commits
- One feature branch created and merged

**Technical Requirements:**
- Run `git init`, `git add .`, `git commit`
- Use branches (e.g., `feature/exceptions`)
- Merge via `git merge`

---

#### Epic 5: Menu Error Handling

**US-5.1: Handle Menu Errors**

> As a user, I want the menu to remain functional after invalid inputs.

**Acceptance Criteria:**
- Program does not crash on invalid entry
- Error message and retry prompt displayed

**Technical Requirements:**
- Use input validation and try-catch in `ConsoleMenu`
- Implement looping until valid entry is provided

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
│   │   ├── RegularUser.java
│   │   ├── AdminUser.java
│   │   └── StatusReport.java
│   │
│   ├── interfaces/
│   │   └── Completable.java
│   │
│   ├── services/
│   │   ├── ProjectService.java
│   │   ├── TaskService.java
│   │   └── ReportService.java
│   │
│   └── utils/
│       ├── ConsoleMenu.java
│       ├── ValidationUtils.java
│       └── exceptions/
│           ├── InvalidInputException.java
│           ├── TaskNotFoundException.java
│           └── EmptyProjectException.java
│
├── test/
│   ├── ProjectTests.java
│   ├── TaskTests.java
│   └── ValidationTests.java
│
├── docs/
│   ├── class-diagram.png
│   └── design-decisions.md
│
└── README.md
```

---

### Implementation Phases

#### Phase 1: Refactor Existing Code (1–2 hours)

**Tasks:**
- Review Lab 1 code
- Apply SOLID and naming best practices
- Separate concerns into services and utils

**Deliverables:** Refactored, readable code with consistent structure.

#### Phase 2: Add Exception Handling (2 hours)

**Tasks:**
- Create custom exception classes
- Add try-catch logic around input operations

**Deliverables:** Program handles invalid inputs gracefully without crashing.

#### Phase 3: JUnit Testing (2 hours)

**Tasks:**
- Write unit tests for key methods
- Run tests in IntelliJ using JUnit 5

**Deliverables:** All tests passing; test coverage for critical logic.

#### Phase 4: Git Version Control (1–2 hours)

**Tasks:**
- Initialize Git repository
- Commit changes incrementally
- Push to GitHub and create branches for features

**Deliverables:** Organized commit history with proper branch merging.

---

### Minimum Requirements Checklist

- [ ] JDK 21 and IntelliJ IDEA installed and configured
- [ ] Refactored code from Lab 1 with clean structure
- [ ] At least 3 custom exception classes implemented
- [ ] All exceptions properly handled via try-catch
- [ ] At least 3 JUnit test cases passing successfully
- [ ] Meaningful variable and method names used throughout
- [ ] Methods follow Single Responsibility Principle
- [ ] Git repository initialized and hosted on GitHub
- [ ] At least 3 commits with clear messages
- [ ] Feature branch created and merged successfully
- [ ] Console menu remains functional after errors
- [ ] README updated with refactoring and Git instructions
- [ ] All previous Lab 1 features remain functional

---

### Grading Rubric

| Criteria | Points | Excellent (90–100%) | Good (75–89%) | Satisfactory (60–74%) |
|---|---|---|---|---|
| Code Refactoring & Clean Code | 20 | All classes follow SOLID principles; excellent naming; no duplication; methods concise and readable | Good structure; minor naming issues; few duplications | Some refactoring done; inconsistent style and naming |
| Exception Handling | 20 | Robust try-catch blocks; custom exceptions implemented; error handling enhances stability | Basic exception handling; covers main failure points | Minimal exception use or only generic catch blocks |
| Testing & Coverage | 20 | ≥ 3 comprehensive JUnit tests; high coverage; clear assertions; edge cases tested | Some tests working; limited coverage; minor failures | Few or incomplete tests with weak assertions |
| Git Version Control | 15 | Proper repo structure; multiple commits with messages; branches merged cleanly; frequent pushes | Repo created; few commits; limited branching | Repo missing or poor commit history |
| Functionality & Stability | 15 | All features functional with graceful error handling; clean UI flow; stable execution | Minor bugs or UI issues; mostly functional | Core features work but frequent errors or crashes |
| Data Structures & Algorithms (DSA) | 10 | Efficient data organization and retrieval within refactored code; optimized logic in tests; shows understanding of algorithmic efficiency | Proper use of data structures in refactoring; minor inefficiencies | Limited or inefficient data handling; weak algorithmic structure |
| **Total** | **100** | | | |

---

### Submission Requirements

**Required Deliverables:**

Public GitHub Repository containing:
- All source code (`/src`, `/test`)
- `README.md` with setup and Git instructions
- JUnit test results screenshot (optional)

**Documentation must include:**
- Setup and run instructions
- Feature summary mapped to user stories
- Class diagram and refactoring explanation
- Commit log snapshot showing version control usage

**Submission Link:** Please fill out this form *(insert actual form link here)*

---

### Testing the Application

#### Test Scenario 1: Refactored Project Creation
1. Run the refactored application
2. Select option 1 (Add Project)
3. Enter valid details for a Software Project
4. Verify constructors and encapsulation work correctly (no direct field access)
5. Confirm ID auto-generates (e.g., PRJ001)
6. Check logs or console output for clean, formatted messages

#### Test Scenario 2: Add Task with Exception Handling
1. Select option 3 (Add Task)
2. Enter invalid project ID (e.g., PRJ999)
3. Verify custom exception displays user-friendly error message
4. Enter valid project ID and task details
5. Confirm successful task creation and no unhandled exceptions

#### Test Scenario 3: View Projects (After Refactoring)
1. Select option 2 (View Projects)
2. Verify that the refactored structure displays data neatly
3. Check tasks associated with each project load properly
4. Confirm no redundant or duplicate display entries

#### Test Scenario 4: Calculate Completion Percentage (Refactored Logic)
1. Select option 6 (Calculate Project Completion)
2. Enter valid Project ID
3. Verify accurate completion percentage after code refactoring
4. Check that calculations are performed in a dedicated method/class
5. Confirm clear and readable output formatting

#### Test Scenario 5: Exception Handling for Invalid Inputs
1. Enter invalid options (letters for numeric input, negative hours, etc.)
2. Verify input validation prevents crashes
3. Confirm appropriate custom exceptions or fallback messages display
4. Check that retry prompts appear correctly

#### Test Scenario 6: Run JUnit Tests
1. Open the JUnit test class in the IDE
2. Run test methods for Project creation, Task addition, and completion calculation
3. Verify all tests pass successfully
4. Confirm proper assertions (e.g., expected vs actual completion %)
5. Check test coverage summary

#### Test Scenario 7: Git Commit and Branch Workflow
1. Initialize Git repository if not done
2. Make initial commit for the refactored code
3. Create new branch `feature/task-validation`
4. Add validation updates and commit
5. Merge back into main branch without conflicts
6. Verify commit history shows meaningful messages

#### Test Scenario 8: Git Push and Remote Verification
1. Push changes to remote repository (e.g., GitHub)
2. Confirm commits reflect online with correct timestamps
3. Verify README and `.gitignore` files are included
4. Check that teammates can clone and run project successfully

#### Test Scenario 9: Code Cleanliness and Comments Check
1. Open source files (`Project.java`, `Task.java`, `Main.java`)
2. Verify consistent indentation and naming conventions
3. Confirm presence of JavaDoc comments on methods
4. Check for absence of dead code or unused imports
