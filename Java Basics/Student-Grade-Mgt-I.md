# Student Grade Management System

**Complexity:** Medium
**Time Estimate:** 10 hours

---

## Project Objectives

By completing this project, you will be able to:

- Apply OOP principles (encapsulation, inheritance, polymorphism) to design Java classes and interfaces for real-world problems
- Create well-structured applications integrating primitive data types, control structures, and custom objects
- Analyze class relationships to choose between inheritance, composition, abstract classes, and interfaces
- Evaluate code quality using proper encapsulation, naming conventions, and OOP best practices
- Apply polymorphic behavior with method overriding to build flexible, extensible code

---

## What You'll Build

A console application for managing student grades with these features:

### Core Features

- **Add Student** – Register new students in the system
- **View Students** – Display all students with their details
- **Record Grade** – Add grades for students in different subjects
- **View Grade Report** – Display grade history for a student
- **Simple Menu** – Navigate through options

### Student Types

| Type | Details |
|---|---|
| Regular Student | Standard grading (passing grade: 50%) |
| Honors Student | Higher standards (passing grade: 60%, eligible for honors recognition) |

### Subject Types

| Type | Details |
|---|---|
| Core Subject | Mandatory subjects (Mathematics, English, Science) |
| Elective Subject | Optional subjects (Music, Art, Physical Education) |

---

## Console Output Examples

### Screenshot 1: Main Menu

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

### Screenshot 2: View Students

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

### Screenshot 3: Add Student (Regular)

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

### Screenshot 4: Add Student (Honors)

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

### Screenshot 5: Record Grade (Core Subject)

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

### Screenshot 6: Record Grade (Elective Subject)

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

### Screenshot 7: View Grade Report (Empty)

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

### Screenshot 8: View Grade Report (With Records)

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

### Screenshot 9: Exit Application

```
Enter choice: 5

Thank you for using Student Grade Management System!
Goodbye!
```

---

## User Stories

### US-1: View Students

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

### US-2: Add Student

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

### US-3: Record Grade

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

### US-4: View Grade Report

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

### US-5: Simple Menu Navigation

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

## Minimum Requirements

- [ ] All 9 required classes implemented
- [ ] All 5 user stories working
- [ ] Static counters work correctly for ID generation
- [ ] Use arrays to manage and retrieve students and grades
- [ ] Application runs without errors
- [ ] Input validation implemented
- [ ] Grade history tracks all operations

---

## Classes (9 total)

- `Student` (abstract), `RegularStudent`, `HonorsStudent`
- `Subject` (abstract), `CoreSubject`, `ElectiveSubject`
- `Gradable` (interface)
- `Grade`, `StudentManager`, `GradeManager`
- `Main`

---

## Features Summary

| Feature | Details |
|---|---|
| View Students | Display 5 students (3 Regular, 2 Honors) |
| Add Student | Both types with confirmation |
| Record Grade | Core and elective subjects |
| View Grade Report | Grade history per student |
| Menu Navigation | Simple console menu |

---

## OOP Principles

- Private fields with public getters/setters
- Inheritance (`Student` & `Subject` hierarchies)
- Abstract classes and methods
- Interface implementation (`Gradable`)
- Method overriding (`displayStudentDetails`, `getStudentType`, etc.)
- Polymorphism (treating `RegularStudent` and `HonorsStudent` as `Student`)
- Composition (`StudentManager` has Student array, `GradeManager` has Grade array)
- Static members (Student counter, Grade counter)

---

## Grading Rubric

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

## Testing the Application

### Test Scenario 1: View Students
1. Run application
2. Select option 2 (View Students)
3. Verify 5 students display with correct information
4. Check Regular students show 50% passing grade
5. Check Honors students show 60% passing grade and honors eligibility
6. Verify total students and average class grade calculations

### Test Scenario 2: Add Regular Student
1. Select option 1 (Add Student)
2. Enter student details (name, age, email, phone)
3. Select Regular Student type
4. Verify unique student ID is generated (STU001, STU002, etc.)
5. Verify confirmation displays all details
6. Verify passing grade shows 50%

### Test Scenario 3: Add Honors Student
1. Select option 1 (Add Student)
2. Enter student details
3. Select Honors Student type
4. Verify honors eligibility is shown
5. Verify passing grade shows 60%

### Test Scenario 4: Record Grade (Core Subject)
1. Add at least one student first
2. Select option 3 (Record Grade)
3. Enter valid student ID
4. Select Core Subject
5. Choose a core subject (Mathematics, English, or Science)
6. Enter grade (75)
7. Verify grade ID is generated
8. Confirm grade

### Test Scenario 5: Record Grade (Elective Subject)
1. Select option 3 (Record Grade)
2. Enter valid student ID
3. Select Elective Subject
4. Choose an elective (Music, Art, or Physical Education)
5. Enter grade (88)
6. Verify transaction succeeds

### Test Scenario 6: Grade Validation
1. Select option 3 (Record Grade)
2. Enter student ID
3. Try to enter grade < 0 → verify system rejects it
4. Try to enter grade > 100 → verify system rejects it
5. Enter valid grade (0–100) → verify system accepts it

### Test Scenario 7: View Grade Report (Empty)
1. Add new student
2. Select option 4 (View Grade Report)
3. Enter new student ID
4. Verify "No grades recorded" message displays

### Test Scenario 8: View Grade Report (With Records)
1. Record 3–5 grades for one student (mix of core and elective)
2. Select option 4 (View Grade Report)
3. Enter student ID
4. Verify all grades display correctly
5. Verify averages calculate correctly (core, elective, overall)
6. Verify passing status is correct

### Test Scenario 9: Honors Eligibility Check
1. Add Honors student
2. Record grades averaging >= 85% → view student listing → verify "Honors Eligible" appears
3. Record grades averaging < 85% → view student listing → verify honors eligibility changes

### Test Scenario 10: ID Auto-generation
1. Create 3 students
2. Verify student IDs are STU001, STU002, STU003
3. Record 3 grades
4. Verify grade IDs are GRD001, GRD002, GRD003
5. Confirm IDs remain unique within the same session

---

**Submission Link:** Submit your project here: [Tally](#)
