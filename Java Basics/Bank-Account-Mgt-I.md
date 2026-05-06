---

## Bank Account Management
---

### Project Objectives

By completing this project, you will be able to:

- Apply OOP principles (encapsulation, inheritance, polymorphism) to design Java classes and interfaces for real-world problems
- Create well-structured applications integrating primitive data types, control structures, and custom objects
- Analyze class relationships to choose between inheritance, composition, abstract classes, and interfaces
- Evaluate code quality using proper encapsulation, naming conventions, and OOP best practices
- Apply polymorphic behavior with method overriding to build flexible, extensible code
- Apply fundamental Data Structures and Algorithms concepts to manage, search, and organize account and transaction data efficiently

---

### What You'll Build

A console application with these features:

#### Core Features

- **Create Account** – Register new bank accounts for customers
- **View Accounts** – Display all accounts with their details
- **Process Transaction** – Deposit or withdraw money from accounts
- **View Transactions** – Display transaction history for an account
- **Simple Menu** – Navigate through options

#### Account Types

| Type | Details |
|---|---|
| Savings Account | Earns interest (interest rate: 3.5% annually, minimum balance: $500) |
| Checking Account | No interest, has overdraft limit (overdraft limit: $1,000, monthly fee: $10) |

#### Customer Types

| Type | Details |
|---|---|
| Regular Customer | Standard banking services |
| Premium Customer | Higher transaction limits, waived fees (minimum balance: $10,000, no monthly fees, priority service) |

---

### Console Output Examples

#### Screenshot 1: Main Menu

```
╔════════════════════════════════════════════╗
║   BANK ACCOUNT MANAGEMENT - MAIN MENU      ║
╚════════════════════════════════════════════╝

1. Create Account
2. View Accounts
3. Process Transaction
4. View Transaction History
5. Exit

Enter choice: _
```

#### Screenshot 2: View Accounts

```
Enter choice: 2

ACCOUNT LISTING
──────────────────────────────────────────────────────────────────────────
ACC NO   | CUSTOMER NAME     | TYPE              | BALANCE      | STATUS
──────────────────────────────────────────────────────────────────────────
ACC001   | John Smith        | Savings           | $5,250.00    | Active
         | Interest Rate: 3.5% | Min Balance: $500.00
──────────────────────────────────────────────────────────────────────────
ACC002   | Sarah Johnson     | Checking          | $3,450.00    | Active
         | Overdraft Limit: $1,000.00 | Monthly Fee: $10.00
──────────────────────────────────────────────────────────────────────────
ACC003   | Michael Chen      | Savings           | $15,750.00   | Active
         | Interest Rate: 3.5% | Min Balance: $500.00
──────────────────────────────────────────────────────────────────────────
ACC004   | Emily Brown       | Checking          | $890.00      | Active
         | Overdraft Limit: $1,000.00 | Monthly Fee: $10.00
──────────────────────────────────────────────────────────────────────────
ACC005   | David Wilson      | Savings           | $25,300.00   | Active
         | Interest Rate: 3.5% | Min Balance: $500.00
──────────────────────────────────────────────────────────────────────────

Total Accounts: 5
Total Bank Balance: $50,640.00

Press Enter to continue...
```

#### Screenshot 3: Create Account (Savings)

```
Enter choice: 1

ACCOUNT CREATION
─────────────────────────────────────────────

Enter customer name: Robert Martinez
Enter customer age: 35
Enter customer contact: +1-555-7890
Enter customer address: 123 Oak Street, Springfield

Customer type:
1. Regular Customer (Standard banking services)
2. Premium Customer (Enhanced benefits, min balance $10,000)

Select type (1-2): 1

Account type:
1. Savings Account (Interest: 3.5%, Min Balance: $500)
2. Checking Account (Overdraft: $1,000, Monthly Fee: $10)

Select type (1-2): 1

Enter initial deposit amount: $2500

✓ Account created successfully!
  Account Number: ACC006
  Customer: Robert Martinez (Regular)
  Account Type: Savings
  Initial Balance: $2,500.00
  Interest Rate: 3.5%
  Minimum Balance: $500.00
  Status: Active

Press Enter to continue...
```

#### Screenshot 4: Create Account (Premium Customer + Checking)

```
Enter choice: 1

ACCOUNT CREATION
─────────────────────────────────────────────

Enter customer name: Jennifer Lee
Enter customer age: 42
Enter customer contact: +1-555-4321
Enter customer address: 456 Maple Avenue, Springfield

Customer type:
1. Regular Customer (Standard banking services)
2. Premium Customer (Enhanced benefits, min balance $10,000)

Select type (1-2): 2

Account type:
1. Savings Account (Interest: 3.5%, Min Balance: $500)
2. Checking Account (Overdraft: $1,000, Monthly Fee: $10)

Select type (1-2): 2

Enter initial deposit amount: $15000

✓ Account created successfully!
  Account Number: ACC007
  Customer: Jennifer Lee (Premium)
  Account Type: Checking
  Initial Balance: $15,000.00
  Overdraft Limit: $1,000.00
  Monthly Fee: $0.00 (WAIVED - Premium Customer)
  Status: Active

Press Enter to continue...
```

#### Screenshot 5: Process Transaction (Deposit)

```
Enter choice: 3

PROCESS TRANSACTION
─────────────────────────────────────────────

Enter Account Number: ACC001

Account Details:
Customer: John Smith
Account Type: Savings
Current Balance: $5,250.00

Transaction type:
1. Deposit
2. Withdrawal

Select type (1-2): 1

Enter amount: $1500

TRANSACTION CONFIRMATION
─────────────────────────────────────────────
Transaction ID: TXN001
Account: ACC001
Type: DEPOSIT
Amount: $1,500.00
Previous Balance: $5,250.00
New Balance: $6,750.00
Date/Time: 30-10-2025 10:30 AM
─────────────────────────────────────────────

Confirm transaction? (Y/N): Y

✓ Transaction completed successfully!

Press Enter to continue...
```

#### Screenshot 6: Process Transaction (Withdrawal)

```
Enter choice: 3

PROCESS TRANSACTION
─────────────────────────────────────────────

Enter Account Number: ACC002

Account Details:
Customer: Sarah Johnson
Account Type: Checking
Current Balance: $3,450.00

Transaction type:
1. Deposit
2. Withdrawal

Select type (1-2): 2

Enter amount: $500

TRANSACTION CONFIRMATION
─────────────────────────────────────────────
Transaction ID: TXN002
Account: ACC002
Type: WITHDRAWAL
Amount: $500.00
Previous Balance: $3,450.00
New Balance: $2,950.00
Date/Time: 30-10-2025 11:15 AM
─────────────────────────────────────────────

Confirm transaction? (Y/N): Y

✓ Transaction completed successfully!

Press Enter to continue...
```

#### Screenshot 7: View Transaction History (Empty)

```
Enter choice: 4

VIEW TRANSACTION HISTORY
─────────────────────────

Enter Account Number: ACC005

Account: ACC005 - David Wilson
Account Type: Savings
Current Balance: $25,300.00

─────────────────────────────────────────────
No transactions recorded for this account.
─────────────────────────────────────────────

Press Enter to continue...
```

#### Screenshot 8: View Transaction History (With Records)

```
Enter choice: 4

VIEW TRANSACTION HISTORY
──────────────────────────

Enter Account Number: ACC001

Account: ACC001 - John Smith
Account Type: Savings
Current Balance: $6,750.00

TRANSACTION HISTORY
───────────────────────────────────────────────────────────────────────
TXN ID  | DATE/TIME           | TYPE       | AMOUNT      | BALANCE
───────────────────────────────────────────────────────────────────────
TXN001  | 30-10-2025 10:30 AM | DEPOSIT    | +$1,500.00  | $6,750.00
TXN002  | 28-10-2025 02:15 PM | WITHDRAWAL | -$750.00    | $5,250.00
TXN003  | 25-10-2025 09:45 AM | DEPOSIT    | +$2,000.00  | $6,000.00
TXN004  | 20-10-2025 03:30 PM | WITHDRAWAL | -$500.00    | $4,000.00
───────────────────────────────────────────────────────────────────────

Total Transactions: 4
Total Deposits: $3,500.00
Total Withdrawals: $1,250.00
Net Change: +$2,250.00

Press Enter to continue...
```

#### Screenshot 9: Exit Application

```
Enter choice: 5

Thank you for using Bank Account Management System!
Goodbye!
```

---

### User Stories

#### US-1: View Accounts

> **As a** bank staff member
> **I want to** view all bank accounts
> **So that** I can see account details and balances

**Acceptance Criteria:**
- Display minimum 5 accounts (3 Savings, 2 Checking)
- Show account number, customer name, type, balance, and status
- Savings accounts show interest rate and minimum balance
- Checking accounts show overdraft limit and monthly fee
- Display total accounts and total bank balance

**Classes to Create:**

**`Account` (abstract class)**
- Private fields: `accountNumber` (String), `customer` (Customer), `balance` (double), `status` (String)
- Static field: `accountCounter` (int) – for generating unique account numbers
- Constructor, getters, setters
- Abstract method: `displayAccountDetails()`
- Abstract method: `getAccountType()`
- Methods: `deposit(double amount)`, `withdraw(double amount)`

**`SavingsAccount extends Account`**
- Private fields: `interestRate` (double), `minimumBalance` (double)
- Constructor (sets interest rate to 3.5%, minimum balance to $500)
- Override `displayAccountDetails()` to show account info + interest details
- Override `getAccountType()` to return `"Savings"`
- Override `withdraw()` to check minimum balance
- Method: `calculateInterest()` – returns interest earned

**`CheckingAccount extends Account`**
- Private fields: `overdraftLimit` (double), `monthlyFee` (double)
- Constructor (sets overdraft limit to $1,000, monthly fee to $10)
- Override `displayAccountDetails()` to show account info + overdraft details
- Override `getAccountType()` to return `"Checking"`
- Override `withdraw()` to allow overdraft up to limit
- Method: `applyMonthlyFee()` – deducts monthly fee from balance

---

#### US-2: Create Account

> **As a** bank staff member
> **I want to** create new bank accounts
> **So that** customers can start banking

**Acceptance Criteria:**
- Capture customer details (name, age, contact, address)
- Support two customer types: Regular and Premium
- Support two account types: Savings and Checking
- Premium customers have waived monthly fees
- Auto-generate unique account number
- Require initial deposit
- Display confirmation with all details

**Classes to Create:**

**`Customer` (abstract class)**
- Private fields: `customerId` (String), `name` (String), `age` (int), `contact` (String), `address` (String)
- Static field: `customerCounter` (int) – for generating unique IDs
- Constructor, getters, setters
- Abstract method: `displayCustomerDetails()`
- Abstract method: `getCustomerType()`

**`RegularCustomer extends Customer`**
- Constructor accepting name, age, contact, address
- Override `displayCustomerDetails()` to show customer info
- Override `getCustomerType()` to return `"Regular"`

**`PremiumCustomer extends Customer`**
- Private field: `minimumBalance` (double) – minimum to maintain premium status ($10,000)
- Constructor accepting name, age, contact, address
- Getter and setter for minimum balance
- Override `displayCustomerDetails()` to show customer info + premium benefits
- Override `getCustomerType()` to return `"Premium"`
- Method: `hasWaivedFees()` – returns `true`

---

#### US-3: Process Transaction

> **As a** bank staff member
> **I want to** process deposits and withdrawals
> **So that** customers can access their money

**Acceptance Criteria:**
- User enters account number
- Validate that account exists
- Allow selection of transaction type (deposit/withdrawal)
- For deposits: accept any positive amount
- For withdrawals: check sufficient balance (or overdraft for checking)
- For savings withdrawals: ensure minimum balance is maintained
- Generate unique transaction ID
- Update account balance
- Show confirmation before finalizing

**Classes to Create:**

**`Transactable` (interface)**
- Method: `processTransaction(double amount, String type)` – returns boolean

**`Transaction`**
- Static field: `transactionCounter` (int) – for generating unique IDs
- Private fields: `transactionId` (String), `accountNumber` (String), `type` (String), `amount` (double), `balanceAfter` (double), `timestamp` (String)
- Constructor accepting account number, type, amount, balance after transaction
- Auto-generates transaction ID (TXN001, TXN002, etc.)
- Auto-generates timestamp
- Getters for all fields
- Method: `displayTransactionDetails()`

**`AccountManager`** (uses composition)
- Private field: `accounts` (Account array, size 50)
- Private field: `accountCount` (int) – tracks number of accounts
- Methods:
  - `addAccount(Account)` – adds account to array
  - `findAccount(String accountNumber)` – returns Account or null
  - `viewAllAccounts()` – displays all accounts
  - `getTotalBalance()` – sums all account balances
  - `getAccountCount()` – returns number of accounts

---

#### US-4: View Transaction History

> **As a** bank staff member
> **I want to** view transaction history for an account
> **So that** I can track account activity

**Acceptance Criteria:**
- Display all transactions for a specific account
- Show transaction ID, date/time, type, amount, and balance after transaction
- Display summary: total deposits, total withdrawals, net change
- Handle accounts with no transactions
- Transactions displayed in reverse chronological order (newest first)

**Classes to Create:**

**`TransactionManager`** (uses composition)
- Private field: `transactions` (Transaction array, size 200)
- Private field: `transactionCount` (int) – tracks number of transactions
- Methods:
  - `addTransaction(Transaction)` – adds transaction to array
  - `viewTransactionsByAccount(String accountNumber)` – displays transactions for account
  - `calculateTotalDeposits(String accountNumber)` – sums deposits
  - `calculateTotalWithdrawals(String accountNumber)` – sums withdrawals
  - `getTransactionCount()` – returns total transaction count

---

#### US-5: Simple Menu Navigation

> **As a** user
> **I want to** navigate through menu options
> **So that** I can use all features

**Acceptance Criteria:**
- Display clear menu with 5 options
- Accept and validate user input
- Execute selected option
- Loop until user exits
- Handle invalid input gracefully

---

### Minimum Requirements

- All 11 required classes implemented
- All 5 user stories working
- Static counters work correctly for ID generation
- Use appropriate data structures to manage and retrieve accounts and transactions efficiently (e.g., arrays or lists)
- Application runs without errors
- Input validation implemented
- Transaction history tracks all operations
- Minimum balance enforced for savings accounts
- Overdraft limit enforced for checking accounts
- README.md included
- GitHub repository is public
- Repository link submitted

---

### Classes (11 total)

- `Account` (abstract), `SavingsAccount`, `CheckingAccount`
- `Customer` (abstract), `RegularCustomer`, `PremiumCustomer`
- `Transactable` (interface)
- `Transaction`, `AccountManager`, `TransactionManager`
- `Main`

---

### Features Summary

| Feature | Details |
|---|---|
| View Accounts | Display 5 accounts (3 Savings, 2 Checking) |
| Create Account | Both types with customer linking |
| Process Transactions | Deposits and withdrawals |
| View History | Transaction history per account |
| Menu Navigation | Simple console menu |

---

### OOP Principles

- Private fields with public getters/setters
- Inheritance (`Account` & `Customer` hierarchies)
- Abstract classes and methods
- Interface implementation (`Transactable`)
- Method overriding (`displayAccountDetails`, `getAccountType`, etc.)
- Composition (`AccountManager` has Account array, `TransactionManager` has Transaction array)
- Static members (Account counter, Customer counter, Transaction counter)

---

### Data Structures & Algorithms (DSA)

- Apply fundamental DSA concepts to manage, search, and organize account and transaction data efficiently
- Apply basic search algorithms (e.g., linear search) to locate accounts and transactions by ID
- Implement simple sorting logic (optional) for displaying transactions or accounts in a defined order (e.g., newest first)
- Demonstrate understanding of time complexity when selecting or designing structures for managing data

---

### Grading Rubric

| Criteria | Points | What We're Looking For |
|---|---|---|
| OOP Principles | 25 | Encapsulation (private fields), inheritance (2 hierarchies), polymorphism (method overriding), abstraction (abstract classes + interface), composition (Manager classes) |
| Functionality | 25 | All 5 user stories work: view accounts, create accounts, process transactions, view history, menu navigation |
| Class Design | 15 | All 11 required classes created, proper relationships, appropriate use of abstract classes and interfaces, correct use of static fields for ID generation |
| DSA | 15 | Proper use of data structures for account and transaction management, correct application of search and iteration algorithms, code efficiency and clarity |
| Code Quality | 10 | Clean code, proper naming, good formatting, input validation, no errors |
| Documentation | 10 | README with setup instructions, code comments for complex logic, clear user prompts |
| **Total** | **100** | |

---

### Testing the Application

#### Test Scenario 1: View Accounts
1. Run application
2. Select option 2 (View Accounts)
3. Verify 5 accounts display with correct information
4. Check Savings accounts show 3.5% interest rate and $500 minimum balance
5. Check Checking accounts show $1,000 overdraft and $10 monthly fee
6. Verify total accounts and total balance calculations

#### Test Scenario 2: Create Savings Account (Regular Customer)
1. Select option 1 (Create Account)
2. Enter customer details (name, age, contact, address)
3. Select Regular Customer type
4. Select Savings Account type
5. Enter initial deposit ($1,000)
6. Verify unique account number is generated (ACC001, ACC002, etc.)
7. Verify confirmation displays all details

#### Test Scenario 3: Create Checking Account (Premium Customer)
1. Select option 1 (Create Account)
2. Enter customer details
3. Select Premium Customer type
4. Select Checking Account type
5. Enter initial deposit ($15,000)
6. Verify monthly fee is waived in confirmation

#### Test Scenario 4: Process Deposit
1. Create at least one account first
2. Select option 3 (Process Transaction)
3. Enter valid account number
4. Select Deposit
5. Enter amount ($500)
6. Verify transaction ID is generated
7. Verify balance updates correctly
8. Confirm transaction

#### Test Scenario 5: Process Withdrawal (Savings – Minimum Balance Check)
1. Select option 3 (Process Transaction)
2. Enter savings account number
3. Select Withdrawal
4. Try to withdraw amount that would go below minimum balance
5. Verify system prevents withdrawal
6. Try valid withdrawal amount
7. Verify transaction succeeds

#### Test Scenario 6: Process Withdrawal (Checking – Overdraft)
1. Select option 3 (Process Transaction)
2. Enter checking account number with balance $500
3. Select Withdrawal
4. Enter $1,200 (within overdraft limit of $1,000)
5. Verify transaction succeeds with negative balance
6. Try withdrawal exceeding overdraft limit
7. Verify system prevents withdrawal

#### Test Scenario 7: View Transaction History (Empty)
1. Create new account
2. Select option 4 (View Transaction History)
3. Enter new account number
4. Verify "No transactions" message displays

#### Test Scenario 8: View Transaction History (With Records)
1. Process 3–4 transactions on one account
2. Select option 4 (View Transaction History)
3. Enter account number
4. Verify all transactions display correctly
5. Verify summary calculations (total deposits, withdrawals, net change)

#### Test Scenario 9: ID Auto-generation
1. Create 3 accounts
2. Verify account numbers are ACC001, ACC002, ACC003
3. Process 3 transactions
4. Verify transaction IDs are TXN001, TXN002, TXN003
5. Verify customer IDs are CUS001, CUS002, CUS003

---
---

## Module 1.2: Student Grade Management System

**Complexity:** Medium
**Time Estimate:** 10 hours

---

### Objectives

By completing this project, you will be able to:

- Apply OOP principles (encapsulation, inheritance, polymorphism) to design Java classes and interfaces for real-world problems
- Create well-structured applications integrating primitive data types, control structures, and custom objects
- Analyze class relationships to choose between inheritance, composition, abstract classes, and interfaces
- Evaluate code quality using proper encapsulation, naming conventions, and OOP best practices
- Apply polymorphic behavior with method overriding to build flexible, extensible code

---

### What You'll Build

A console application for managing student grades with these features:

#### Core Features

- **Add Student** – Register new students in the system
- **View Students** – Display all students with their details
- **Record Grade** – Add grades for students in different subjects
- **View Grade Report** – Display grade history for a student
- **Simple Menu** – Navigate through options

#### Student Types

| Type | Details |
|---|---|
| Regular Student | Standard grading (passing grade: 50%) |
| Honors Student | Higher standards (passing grade: 60%, eligible for honors recognition) |

#### Subject Types

| Type | Details |
|---|---|
| Core Subject | Mandatory subjects (Mathematics, English, Science) |
| Elective Subject | Optional subjects (Music, Art, Physical Education) |

---

### Console Output Examples

#### Screenshot 1: Main Menu

```
╔════════════════════════════════════════════╗
║   STUDENT GRADE MANAGEMENT - MAIN MENU     ║
╚════════════════════════════════════════════╝

1. Add Student
2. View Students
3. Record Grade
4. View Grade Report
5. Exit

Enter choice: _
```

#### Screenshot 2: View Students

```
Enter choice: 2

STUDENT LISTING
──────────────────────────────────────────────────────────────────────────
STU ID   | NAME              | TYPE         | AVG GRADE | STATUS
──────────────────────────────────────────────────────────────────────────
STU001   | Alice Johnson     | Regular      | 78.5%     | Passing
         | Enrolled Subjects: 5 | Passing Grade: 50%
──────────────────────────────────────────────────────────────────────────
STU002   | Bob Smith         | Honors       | 85.2%     | Passing
         | Enrolled Subjects: 6 | Passing Grade: 60% | Honors Eligible
──────────────────────────────────────────────────────────────────────────
STU003   | Carol Martinez    | Regular      | 45.0%     | Failing
         | Enrolled Subjects: 4 | Passing Grade: 50%
──────────────────────────────────────────────────────────────────────────
STU004   | David Chen        | Honors       | 92.8%     | Passing
         | Enrolled Subjects: 6 | Passing Grade: 60% | Honors Eligible
──────────────────────────────────────────────────────────────────────────
STU005   | Emma Wilson       | Regular      | 67.3%     | Passing
         | Enrolled Subjects: 5 | Passing Grade: 50%
──────────────────────────────────────────────────────────────────────────

Total Students: 5
Average Class Grade: 73.8%

Press Enter to continue...
```

#### Screenshot 3: Add Student (Regular)

```
Enter choice: 1

ADD STUDENT
─────────────────────────────────────────────

Enter student name: Frank Thomas
Enter student age: 16
Enter student email: frank.thomas@school.edu
Enter student phone: +1-555-1234

Student type:
1. Regular Student (Passing grade: 50%)
2. Honors Student (Passing grade: 60%, honors recognition)

Select type (1-2): 1

✓ Student added successfully!
  Student ID: STU006
  Name: Frank Thomas
  Type: Regular
  Age: 16
  Email: frank.thomas@school.edu
  Passing Grade: 50%
  Status: Active

Press Enter to continue...
```

#### Screenshot 4: Add Student (Honors)

```
Enter choice: 1

ADD STUDENT
─────────────────────────────────────────────

Enter student name: Grace Lee
Enter student age: 17
Enter student email: grace.lee@school.edu
Enter student phone: +1-555-5678

Student type:
1. Regular Student (Passing grade: 50%)
2. Honors Student (Passing grade: 60%, honors recognition)

Select type (1-2): 2

✓ Student added successfully!
  Student ID: STU007
  Name: Grace Lee
  Type: Honors
  Age: 17
  Email: grace.lee@school.edu
  Passing Grade: 60%
  Honors Eligible: Yes
  Status: Active

Press Enter to continue...
```

#### Screenshot 5: Record Grade (Core Subject)

```
Enter choice: 3

RECORD GRADE
─────────────────────────────────────────────

Enter Student ID: STU001

Student Details:
Name: Alice Johnson
Type: Regular Student
Current Average: 78.5%

Subject type:
1. Core Subject (Mathematics, English, Science)
2. Elective Subject (Music, Art, Physical Education)

Select type (1-2): 1

Available Core Subjects:
1. Mathematics
2. English
3. Science

Select subject (1-3): 1

Enter grade (0-100): 85

GRADE CONFIRMATION
─────────────────────────────────────────────
Grade ID: GRD001
Student: STU001 - Alice Johnson
Subject: Mathematics (Core)
Grade: 85.0%
Date: 03-11-2025
─────────────────────────────────────────────

Confirm grade? (Y/N): Y

✓ Grade recorded successfully!

Press Enter to continue...
```

#### Screenshot 6: Record Grade (Elective Subject)

```
Enter choice: 3

RECORD GRADE
─────────────────────────────────────────────

Enter Student ID: STU002

Student Details:
Name: Bob Smith
Type: Honors Student
Current Average: 85.2%

Subject type:
1. Core Subject (Mathematics, English, Science)
2. Elective Subject (Music, Art, Physical Education)

Select type (1-2): 2

Available Elective Subjects:
1. Music
2. Art
3. Physical Education

Select subject (1-3): 2

Enter grade (0-100): 92

GRADE CONFIRMATION
─────────────────────────────────────────────
Grade ID: GRD002
Student: STU002 - Bob Smith
Subject: Art (Elective)
Grade: 92.0%
Date: 03-11-2025
─────────────────────────────────────────────

Confirm grade? (Y/N): Y

✓ Grade recorded successfully!

Press Enter to continue...
```

#### Screenshot 7: View Grade Report (Empty)

```
Enter choice: 4

VIEW GRADE REPORT
─────────────────────────────────────────────

Enter Student ID: STU006

Student: STU006 - Frank Thomas
Type: Regular Student
Passing Grade: 50%

─────────────────────────────────────────────
No grades recorded for this student.
─────────────────────────────────────────────

Press Enter to continue...
```

#### Screenshot 8: View Grade Report (With Records)

```
Enter choice: 4

VIEW GRADE REPORT
──────────────────────────

Enter Student ID: STU001

Student: STU001 - Alice Johnson
Type: Regular Student
Current Average: 81.2%
Status: PASSING ✓

GRADE HISTORY
───────────────────────────────────────────────────────────────────────
GRD ID  | DATE       | SUBJECT          | TYPE      | GRADE
───────────────────────────────────────────────────────────────────────
GRD001  | 03-11-2025 | Mathematics      | Core      | 85.0%
GRD002  | 02-11-2025 | English          | Core      | 78.0%
GRD003  | 01-11-2025 | Science          | Core      | 92.0%
GRD004  | 31-10-2025 | Music            | Elective  | 88.0%
GRD005  | 30-10-2025 | Art              | Elective  | 63.0%
───────────────────────────────────────────────────────────────────────

Total Grades: 5
Core Subjects Average: 85.0%
Elective Subjects Average: 75.5%
Overall Average: 81.2%

Performance Summary:
✓ Passing all core subjects
✓ Meeting passing grade requirement (50%)

Press Enter to continue...
```

#### Screenshot 9: Exit Application

```
Enter choice: 5

Thank you for using Student Grade Management System!
Goodbye!
```

---

### User Stories

#### US-1: View Students

> **As a** teacher
> **I want to** view all students
> **So that** I can see their details and performance

**Acceptance Criteria:**
- Display minimum 5 students (3 Regular, 2 Honors)
- Show student ID, name, type, average grade, and status
- Regular students show passing grade of 50%
- Honors students show passing grade of 60% and honors eligibility
- Display total students and average class grade

**Classes to Create:**

**`Student` (abstract class)**
- Private fields: `studentId` (String), `name` (String), `age` (int), `email` (String), `phone` (String), `status` (String)
- Static field: `studentCounter` (int) – for generating unique student IDs
- Constructor, getters, setters
- Abstract method: `displayStudentDetails()`
- Abstract method: `getStudentType()`
- Abstract method: `getPassingGrade()` – returns minimum passing grade
- Method: `calculateAverageGrade()` – returns average of all grades
- Method: `isPassing()` – checks if average meets passing grade

**`RegularStudent extends Student`**
- Private field: `passingGrade` (double) – set to 50.0
- Constructor accepting name, age, email, phone
- Override `displayStudentDetails()` to show student info
- Override `getStudentType()` to return `"Regular"`
- Override `getPassingGrade()` to return `50.0`

**`HonorsStudent extends Student`**
- Private fields: `passingGrade` (double) – set to 60.0, `honorsEligible` (boolean)
- Constructor accepting name, age, email, phone
- Override `displayStudentDetails()` to show student info + honors status
- Override `getStudentType()` to return `"Honors"`
- Override `getPassingGrade()` to return `60.0`
- Method: `checkHonorsEligibility()` – returns true if average >= 85%

---

#### US-2: Add Student

> **As a** teacher
> **I want to** add new students
> **So that** I can track their grades

**Acceptance Criteria:**
- Capture student details (name, age, email, phone)
- Support two student types: Regular and Honors
- Auto-generate unique student ID
- Display confirmation with all details
- Set initial status as "Active"

> No new classes needed – uses Student hierarchy from US-1.

---

#### US-3: Record Grade

> **As a** teacher
> **I want to** record grades for students
> **So that** I can track their performance

**Acceptance Criteria:**
- User enters student ID
- Validate that student exists
- Allow selection of subject type (Core/Elective)
- Select specific subject from available options
- Enter grade (0–100)
- Validate grade is within range
- Generate unique grade ID
- Show confirmation before finalizing

**Classes to Create:**

**`Subject` (abstract class)**
- Private fields: `subjectName` (String), `subjectCode` (String)
- Constructor, getters, setters
- Abstract method: `displaySubjectDetails()`
- Abstract method: `getSubjectType()`

**`CoreSubject extends Subject`**
- Private field: `mandatory` (boolean) – always true
- Constructor accepting subject name and code
- Override `displaySubjectDetails()` to show subject info
- Override `getSubjectType()` to return `"Core"`
- Method: `isMandatory()` – returns true

**`ElectiveSubject extends Subject`**
- Private field: `mandatory` (boolean) – always false
- Constructor accepting subject name and code
- Override `displaySubjectDetails()` to show subject info
- Override `getSubjectType()` to return `"Elective"`
- Method: `isMandatory()` – returns false

**`Gradable` (interface)**
- Method: `recordGrade(double grade)` – returns boolean
- Method: `validateGrade(double grade)` – returns boolean

**`Grade`**
- Static field: `gradeCounter` (int) – for generating unique IDs
- Private fields: `gradeId` (String), `studentId` (String), `subject` (Subject), `grade` (double), `date` (String)
- Constructor accepting student ID, subject, and grade
- Auto-generates grade ID (GRD001, GRD002, etc.)
- Auto-generates date
- Getters for all fields
- Method: `displayGradeDetails()`
- Method: `getLetterGrade()` – converts numeric to letter grade (A, B, C, D, F)

---

#### US-4: View Grade Report

> **As a** teacher
> **I want to** view grade report for a student
> **So that** I can track their progress

**Acceptance Criteria:**
- Display all grades for a specific student
- Show grade ID, date, subject, type, and grade
- Calculate and display averages for core subjects, elective subjects, and overall
- Show performance summary (passing status)
- Handle students with no grades
- Grades displayed in reverse chronological order (newest first)

**Classes to Create:**

**`GradeManager`** (uses composition)
- Private field: `grades` (Grade array, size 200)
- Private field: `gradeCount` (int) – tracks number of grades
- Methods:
  - `addGrade(Grade)` – adds grade to array
  - `viewGradesByStudent(String studentId)` – displays grades for student
  - `calculateCoreAverage(String studentId)` – average of core subjects
  - `calculateElectiveAverage(String studentId)` – average of electives
  - `calculateOverallAverage(String studentId)` – average of all grades
  - `getGradeCount()` – returns total grade count

---

#### US-5: Simple Menu Navigation

> **As a** user
> **I want to** navigate through menu options
> **So that** I can use all features

**Acceptance Criteria:**
- Display clear menu with 5 options
- Accept and validate user input
- Execute selected option
- Loop until user exits
- Handle invalid input gracefully

**Classes to Create:**

**`StudentManager`** (uses composition)
- Private field: `students` (Student array, size 50)
- Private field: `studentCount` (int) – tracks number of students
- Methods:
  - `addStudent(Student)` – adds student to array
  - `findStudent(String studentId)` – returns Student or null
  - `viewAllStudents()` – displays all students
  - `getAverageClassGrade()` – calculates class average
  - `getStudentCount()` – returns number of students

---

### Minimum Requirements

- [ ] All 9 required classes implemented
- [ ] All 5 user stories working
- [ ] Static counters work correctly for ID generation
- [ ] Use arrays to manage and retrieve students and grades
- [ ] Application runs without errors
- [ ] Input validation implemented
- [ ] Grade history tracks all operations

---

### Classes (9 total)

- `Student` (abstract), `RegularStudent`, `HonorsStudent`
- `Subject` (abstract), `CoreSubject`, `ElectiveSubject`
- `Gradable` (interface)
- `Grade`, `StudentManager`, `GradeManager`
- `Main`

---

### OOP Principles

- Private fields with public getters/setters
- Inheritance (`Student` & `Subject` hierarchies)
- Abstract classes and methods
- Interface implementation (`Gradable`)
- Method overriding (`displayStudentDetails`, `getStudentType`, etc.)
- Polymorphism (treating `RegularStudent` and `HonorsStudent` as `Student`)
- Composition (`StudentManager` has Student array, `GradeManager` has Grade array)
- Static members (Student counter, Grade counter)

---

### Grading Rubric

| Criteria | Points | What We're Looking For |
|---|---|---|
| OOP Principles | 25 | Encapsulation (private fields), inheritance (2 hierarchies), polymorphism (method overriding), abstraction (abstract classes + interface), composition (Manager classes) |
| Functionality | 25 | All 5 user stories work: view students, add students, record grades, view reports, menu navigation |
| Class Design | 15 | All 9 required classes created, proper relationships, appropriate use of abstract classes and interfaces, correct use of static fields for ID generation |
| Data Management | 15 | Proper use of arrays for student and grade management, correct application of search and iteration, code efficiency and clarity |
| Code Quality | 10 | Clean code, proper naming, good formatting, input validation, no errors |
| Documentation | 10 | README with setup instructions, code comments for complex logic, clear user prompts |
| **Total** | **100** | |

---

### Testing the Application

#### Test Scenario 1: View Students
1. Run application
2. Select option 2 (View Students)
3. Verify 5 students display with correct information
4. Check Regular students show 50% passing grade
5. Check Honors students show 60% passing grade and honors eligibility
6. Verify total students and average class grade calculations

#### Test Scenario 2: Add Regular Student
1. Select option 1 (Add Student)
2. Enter student details (name, age, email, phone)
3. Select Regular Student type
4. Verify unique student ID is generated (STU001, STU002, etc.)
5. Verify confirmation displays all details
6. Verify passing grade shows 50%

#### Test Scenario 3: Add Honors Student
1. Select option 1 (Add Student)
2. Enter student details
3. Select Honors Student type
4. Verify honors eligibility is shown
5. Verify passing grade shows 60%

#### Test Scenario 4: Record Grade (Core Subject)
1. Add at least one student first
2. Select option 3 (Record Grade)
3. Enter valid student ID
4. Select Core Subject
5. Choose a core subject (Mathematics, English, or Science)
6. Enter grade (75)
7. Verify grade ID is generated
8. Confirm grade

#### Test Scenario 5: Record Grade (Elective Subject)
1. Select option 3 (Record Grade)
2. Enter valid student ID
3. Select Elective Subject
4. Choose an elective (Music, Art, or Physical Education)
5. Enter grade (88)
6. Verify transaction succeeds

#### Test Scenario 6: Grade Validation
1. Select option 3 (Record Grade)
2. Enter student ID
3. Try to enter grade < 0 → verify system rejects it
4. Try to enter grade > 100 → verify system rejects it
5. Enter valid grade (0–100) → verify system accepts it

#### Test Scenario 7: View Grade Report (Empty)
1. Add new student
2. Select option 4 (View Grade Report)
3. Enter new student ID
4. Verify "No grades recorded" message displays

#### Test Scenario 8: View Grade Report (With Records)
1. Record 3–5 grades for one student (mix of core and elective)
2. Select option 4 (View Grade Report)
3. Enter student ID
4. Verify all grades display correctly
5. Verify averages calculate correctly (core, elective, overall)
6. Verify passing status is correct

#### Test Scenario 9: Honors Eligibility Check
1. Add Honors student
2. Record grades averaging >= 85% → view student listing → verify "Honors Eligible" appears
3. Record grades averaging < 85% → view student listing → verify honors eligibility changes

#### Test Scenario 10: Unit Tests Execution
1. Run all JUnit tests: `mvn test` or IDE test runner
2. Verify all 25+ unit tests pass
3. Run integration tests → verify all 10+ integration tests pass
4. Generate coverage report: `mvn jacoco:report`
5. Verify 85%+ coverage achieved
6. Check collections performance tests results
7. Check concurrency tests pass (no race conditions detected)
8. Review test execution time
9. Document any failed tests and reasons

---

**Submission Link:** Submit your project here: [Tally](#)

---
---

## Module 1.3: Task Management System

**Complexity:** Medium
**Time Estimate:** 10 hours
**Technology Stack:** Java 21 (LTS), IntelliJ IDEA Community Edition

---

### Project Overview

Build a console-based Project/Task Management System where users can create projects, add and assign tasks, record task completion status, and calculate completion averages.

This lab focuses on core Java programming and object-oriented principles while storing all data in-memory using arrays (no databases or external dependencies).

The lab serves as the foundation for the multi-week Project Management series. Future labs will gradually enhance this base — replacing arrays with collections, adding file persistence, and integrating user authentication and reporting dashboards.

---

### Learning Objectives

By completing this lab, you will be able to:

- Understand how to design a simple console-based application using core Java
- Apply object-oriented programming principles (encapsulation, inheritance, and polymorphism) to represent projects, tasks, and users
- Use Java arrays, loops, and conditional structures to manage and manipulate data in memory
- Define and extend classes, abstract classes, and interfaces to promote clean, reusable designs
- Demonstrate method overloading and method overriding to implement flexible and polymorphic behaviors
- Design simple menu-driven console interfaces with structured user input validation
- Compute project completion percentages by aggregating data from arrays of task statuses
- Lay the groundwork for future enhancements, where arrays will evolve into Java Collections and file-based data storage

---

### System Features Overview

#### Feature 1: Project Catalog Management
- Create new projects (e.g., `SoftwareProject`, `HardwareProject`)
- View all existing projects with details (ID, name, description, team size, budget, etc.)
- Filter projects by type (software/hardware)
- Display project-specific attributes dynamically

#### Feature 2: Task Operations
- Add tasks to specific projects
- Assign task status (Pending, In Progress, Completed)
- View all tasks per project with progress details
- Update or delete tasks
- Validate inputs to prevent invalid task status or duplicate task names

#### Feature 3: User Management
- Create and manage system users (`RegularUser` and `AdminUser`)
- Assign users to projects or tasks
- Enforce role-based access (Admin can delete/update; Regular can view/add)
- Automatically generate unique user IDs

#### Feature 4: Status Processing & Reporting
- Calculate and display completion averages per project
- Generate status reports (e.g., "Project Alpha is 75% complete")
- Display task statistics: total, completed, and pending counts
- Show per-user performance summaries (future expansion)

#### Feature 5: Menu Navigation & User Experience
- Display a clear main menu and sub-menus for operations
- Validate all user inputs (numbers, text, IDs)
- Provide formatted outputs with clear sections and alignment
- Support graceful exit and return navigation

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

#### 2. Project Catalog Display

```
╔════════════════════════════════════════════╗
║               PROJECT CATALOG              ║
╚════════════════════════════════════════════╝

Filter Options:
1. View All Projects (5)
2. Software Projects Only
3. Hardware Projects Only
4. Search by Budget Range

Enter filter choice: 1

───────────────────────────────────────────────────────────────────────
ID   | PROJECT NAME         | TYPE       | TEAM SIZE | BUDGET
───────────────────────────────────────────────────────────────────────
P001 | Alpha Tracker        | Software   | 5         | $15,000
     | Description: Task tracking app for startups
───────────────────────────────────────────────────────────────────────
P002 | IoT Sensor Kit       | Hardware   | 3         | $10,000
     | Description: Sensor prototype for smart devices
───────────────────────────────────────────────────────────────────────
Enter project ID to view details (or 0 to return): _
```

#### 3. Project Details View

```
╔════════════════════════════════════════════╗
║           PROJECT DETAILS: P001            ║
╚════════════════════════════════════════════╝

Project Name: Alpha Tracker
Type: Software
Team Size: 5
Budget: $15,000

Associated Tasks:
───────────────────────────────────────────────────────────────────────
ID   | TASK NAME          | STATUS
───────────────────────────────────────────────────────────────────────
T001 | Design Database    | Completed
T002 | Implement API      | In Progress
T003 | Write Unit Tests   | Pending
───────────────────────────────────────────────────────────────────────
Completion Rate: 33%

Options:
1. Add New Task
2. Update Task Status
3. Remove Task
4. Back to Main Menu

Enter your choice: _
```

#### 4. Add Task

```
╔════════════════════════════════════════════╗
║               ADD NEW TASK                 ║
╚════════════════════════════════════════════╝

Enter task name: Implement UI
Enter assigned project ID: P001
Enter initial status (Pending/In Progress/Completed): Pending

✓ Task "Implement UI" added successfully to Project P001!
```

#### 5. Update Task Status

```
Enter task ID: T002
Enter new status: Completed

✓ Task "Implement API" marked as Completed.
```

#### 6. Status Report Display

```
╔════════════════════════════════════════════╗
║            PROJECT STATUS REPORT           ║
╚════════════════════════════════════════════╝

───────────────────────────────────────────────────────────────────────
PROJECT ID | PROJECT NAME      | TASKS | COMPLETED | PROGRESS (%)
───────────────────────────────────────────────────────────────────────
P001       | Alpha Tracker     |   4   |    3      |   75%
P002       | IoT Sensor Kit    |   2   |    1      |   50%
───────────────────────────────────────────────────────────────────────
AVERAGE COMPLETION: 62.5%
───────────────────────────────────────────────────────────────────────
```

#### 7. Input Validation Examples

```
Enter project ID: XYZ
❌ Error: Invalid input. Please enter a valid numeric or prefixed ID (e.g., P001).

Enter task status: Done
❌ Error: Invalid status. Please choose from [Pending, In Progress, Completed].

Enter team size: -3
❌ Error: Team size must be greater than 0.

Enter again: 5
✓ Project successfully created.
```

---

### Expected User Workflows

#### Workflow 1: Complete Task Assignment Journey
1. User logs into system
2. System displays the main menu
3. User selects "Manage Projects"
4. User adds a new project ("Alpha Tracker")
5. User adds tasks under that project
6. User updates task statuses
7. System calculates completion average
8. User views report

#### Workflow 2: Project Discovery
1. User selects "Browse Projects"
2. Filters by Software Projects
3. Views detailed project info
4. Adds a new related task
5. Returns to main menu

#### Workflow 3: Task Management
1. User opens "Manage Tasks"
2. Views tasks for selected project
3. Updates task status
4. Deletes outdated tasks
5. System recalculates progress

#### Workflow 4: Status Reporting
1. User opens "View Status Reports"
2. System displays all projects with completion percentages
3. User compares project progress and returns to menu

---

### User Stories

#### Epic 1: Project Catalog Management

**US-1.1: Browse Projects**

> **As a** user
> **I want to** view all available projects with their details
> **So that** I can understand ongoing work

**Acceptance Criteria:**
- Display all projects with ID, name, type, and budget
- Show team size and description
- Support filtering by project type

**Technical Requirements:**
- Create abstract class `Project` with:
  - Private fields: `id`, `name`, `description`, `budget`, `teamSize`
  - Abstract method `getProjectDetails()`
  - Concrete method `displayProject()`
- Implement subclasses `SoftwareProject` and `HardwareProject`
- Store projects in an array (minimum 5)

---

**US-1.2: Search Projects by Budget Range**

> **As a** user
> **I want to** search projects within a specified budget range
> **So that** I can filter based on funding

**Acceptance Criteria:**
- Input min and max budget
- Show projects within range or "No projects found"
- Validate numeric inputs

**Technical Requirements:**
- Use comparison operators and loops
- Use conditionals to check valid range
- Display formatted output using `System.out.printf()`

---

#### Epic 2: Task Operations

**US-2.1: Add Task to Project**

> **As a** user
> **I want to** add tasks under a project
> **So that** I can track progress effectively

**Acceptance Criteria:**
- Assign unique task IDs
- Specify task name and initial status
- Prevent duplicates

**Technical Requirements:**
- Create `Task` class with fields: `id`, `name`, `status`
- Implement interface `Completable` with method `boolean isCompleted()`
- Store tasks in an array within each project

---

**US-2.2: Update Task Status**

> **As a** user
> **I want to** update the status of a task
> **So that** progress reflects accurately

**Acceptance Criteria:**
- Select task by ID
- Choose from allowed statuses
- Update and display success message

**Technical Requirements:**
- Use loops to locate task in project's task array
- Use enums or constants for valid statuses
- Apply encapsulation with proper setters/getters

---

#### Epic 3: User Management

**US-3.1: Create User Profiles**

> **As a** system
> **I want to** create different user roles
> **So that** permissions can vary

**Acceptance Criteria:**
- Create `RegularUser` and `AdminUser` classes
- Assign auto-generated unique IDs
- Display user role when logged in

**Technical Requirements:**
- Abstract `User` class with fields `id`, `name`, `email`, `role`
- Use static counter for ID generation
- Apply inheritance and polymorphism for role behavior

---

#### Epic 4: Status Processing & Reporting

**US-4.1: Calculate Project Completion Average**

> **As a** system
> **I want to** calculate how many tasks are completed per project
> **So that** I can show progress percentage

**Acceptance Criteria:**
- Display total tasks, completed tasks, and percentage
- Handle projects with zero tasks
- Round percentages to 2 decimals

**Technical Requirements:**
- Use arithmetic and conditional operators
- Iterate task arrays to count completions
- Store computed percentages temporarily for reporting

---

#### Epic 5: Menu Navigation & Application Control

**US-5.1: Display Main Menu**

> **As a** user
> **I want to** navigate through clear menu options
> **So that** I can easily use the system

**Acceptance Criteria:**
- Display menu options numbered (1–5)
- Validate choice
- Loop until exit chosen

**Technical Requirements:**
- Use `Scanner` for input
- Implement menu with `switch` or `if-else`
- Wrap in `do-while` loop for continuous running

---

### Project Structure

```
project-management-system/
│
├── src/
│   ├── Main.java                     # Application entry point
│   ├── models/
│   │   ├── Project.java              # Abstract base class
│   │   ├── SoftwareProject.java      # Concrete project type
│   │   ├── HardwareProject.java      # Concrete project type
│   │   ├── Task.java                 # Task model
│   │   ├── User.java                 # Abstract user base
│   │   ├── RegularUser.java          # Concrete user type
│   │   ├── AdminUser.java            # Concrete user type
│   │   └── StatusReport.java         # Status report generation
│   │
│   ├── interfaces/
│   │   └── Completable.java          # Interface for completion logic
│   │
│   ├── services/
│   │   ├── ProjectService.java       # Project operations
│   │   ├── TaskService.java          # Task operations
│   │   └── ReportService.java        # Reporting logic
│   │
│   └── utils/
│       ├── ConsoleMenu.java          # Menu handling
│       └── ValidationUtils.java      # Input validation
│
├── docs/
│   ├── class-diagram.png
│   └── design-decisions.md
│
└── README.md
```

---

### Implementation Phases

#### Phase 1: Foundation Setup (1–2 hours)

**Tasks:**
- Install JDK 21 and IntelliJ IDEA
- Create project folder structure
- Implement `Project` and `User` base classes
- Test object creation with sample data

**Deliverables:**
- Working environment
- Abstract base classes created
- Sample data printed successfully

#### Phase 2: Core Logic Development (2–3 hours)

**Tasks:**
- Implement `Task` and `Completable`
- Add `SoftwareProject` and `HardwareProject` subclasses
- Implement task addition, updates, and completion calculation

**Deliverables:**
- Working project–task relationship
- Completion logic functioning

#### Phase 3: User Interface Integration (2–3 hours)

**Tasks:**
- Implement console menu and navigation
- Handle user inputs and validations
- Display formatted project/task lists
- Integrate reporting logic

**Deliverables:**
- Fully interactive console app
- All user stories are functional

#### Phase 4: Documentation & Finalization (1 hour)

**Tasks:**
- Create README.md with setup and usage guide
- Add class diagram and OOP design rationale
- Final testing and code cleanup

**Deliverables:**
- Complete documentation
- Clean, well-commented codebase

---

### Minimum Requirements Checklist

- [ ] JDK 21 and IntelliJ installed
- [ ] At least 2 project types implemented
- [ ] At least 2 user types implemented
- [ ] Minimum 5 sample projects created
- [ ] Use of arrays for storage
- [ ] Encapsulation applied to all models
- [ ] Abstract classes & interfaces implemented
- [ ] Polymorphism demonstrated
- [ ] Input validation implemented
- [ ] Completion percentage calculation working
- [ ] Console navigation functional
- [ ] README and documentation included

---

### Grading Rubric

| Criteria | Points | Excellent (90–100%) | Good (75–89%) | Satisfactory (60–74%) |
|---|---|---|---|---|
| Development Environment & Basics | 10 | JDK 21 & IntelliJ setup perfect; excellent use of arrays, loops, conditionals | Setup functional, few issues | Basic setup but missing validations |
| Classes, Objects & Encapsulation | 20 | Well-structured classes; perfect encapsulation; clear constructors | Mostly encapsulated, minor design issues | Basic encapsulation; incomplete constructors |
| Inheritance & Polymorphism | 20 | Strong hierarchies for Project/User; clear overriding; polymorphic reporting | Proper inheritance with limited polymorphism | Minimal inheritance demonstration |
| Abstract Classes & Interfaces | 20 | Clear abstract contracts (`Project`, `User`, `Completable`) implemented correctly | Proper but limited use of abstractions | Basic implementation; partial understanding |
| Functionality & Code Quality | 20 | All user stories working; clean code; readable formatting; complete testing | Most features working; well-organized | Core logic functional; partial validation |
| Data Structures & Algorithms (DSA) | 10 | Excellent use of arrays and simple algorithms (search/sort); efficient iteration; clear logic flow with awareness of complexity | Proper array operations; some inefficiencies but logical structure | Basic array handling; repetitive or inefficient logic |
| **Total** | **100** | | | |

---

### Testing the Application

#### Test Scenario 1: View Projects
1. Run application
2. Select option 2 (View Projects)
3. Verify all created projects display with correct details (Project ID, Name, Type, Completion %)
4. Check that Software and Hardware projects are listed separately
5. Verify total projects count displays correctly
6. Confirm data is retrieved from the in-memory array

#### Test Scenario 2: Add Software Project
1. Select option 1 (Add Project)
2. Choose "Software Project" type
3. Enter project details (name, description, duration, budget)
4. Verify unique project ID generated (e.g., PRJ001, PRJ002)
5. Confirm project appears when viewing all projects
6. Ensure data is stored correctly in the array

#### Test Scenario 3: Add Hardware Project
1. Select option 1 (Add Project)
2. Choose "Hardware Project" type
3. Enter details as prompted
4. Verify project is stored with type = "Hardware"
5. Check ID auto-increments from previous project ID
6. Verify total count updates correctly

#### Test Scenario 4: Add Task to Project
1. Select option 3 (Add Task)
2. Choose a project ID to associate task with
3. Enter task details (Task Name, Assigned To, Status, Hours)
4. Verify task is added under correct project in array
5. Confirm Task ID auto-generates (e.g., TSK001, TSK002)

#### Test Scenario 5: View Tasks
1. Select option 4 (View Tasks)
2. Enter a valid Project ID
3. Verify all tasks display with correct information (Name, Status, Hours)
4. Check completed and pending tasks are labeled properly
5. Confirm "No tasks found" message for projects with none

#### Test Scenario 6: Update Task Status
1. Select option 5 (Update Task Status)
2. Enter valid Task ID
3. Change status from "Pending" to "Completed"
4. Verify update reflects in project task list
5. Confirm array data structure updated correctly

#### Test Scenario 7: Calculate Completion Percentage
1. Select option 6 (Calculate Project Completion)
2. Enter valid Project ID
3. Verify correct completion % based on completed vs total tasks
4. Ensure calculated result displays with two decimal places
5. Test with all tasks complete and all tasks pending

#### Test Scenario 8: Handle Invalid Inputs
1. Enter invalid menu option (e.g., 10) → verify "Invalid option" message
2. Enter non-numeric input where number expected → verify application prompts user to re-enter
3. Confirm program does not crash

#### Test Scenario 9: ID Auto-generation
1. Create multiple projects and tasks
2. Verify sequential Project IDs (PRJ001, PRJ002, etc.)
3. Verify sequential Task IDs (TSK001, TSK002, etc.)
4. Confirm IDs remain unique after multiple runs within same session

---

### Submission Requirements

**Required Deliverables:**

Public GitHub Repository containing:
- All source code under `/src`
- `README.md` with setup steps
- UML diagram and design rationale

**Documentation must include:**
- Setup and run instructions
- Feature summary mapped to user stories
- Class diagram showing inheritance and relationships
- Explanation of OOP design choices

