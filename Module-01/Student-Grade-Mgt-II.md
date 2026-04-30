# Student Grade Management System

Student Grade Management System  

Project Objectives  

By completing this project, you will be able to:  

Apply OOP principles (encapsulation, inheritance2, polym2orphism) to design Java classes and interfaces for real-world problems  

Create well-structured applications integrating primitive data types, control structures, and custom objects  

Analyze class relationships to choose between inheritance, composition, abstract classes, and interfaces  

Evaluate code quality using proper encapsulation, naming conventions, and OOP best practices  

Apply polymorphic behavior with method overriding to build flexible, extensible code  

What You'll Build  

A console application for managing student grades with these features:  

Core Features  

Add Student - Register new students in the system  

View Students - Display all students with their details  

Record Grade - Add grades for students in different subjects  

View Grade Report - Display grade history for a student  

Simple Menu - Navigate through options  

Student Types  

Regular Student - standard grading (passing grade: 50%)  

Honors Student - higher standards (passing grade: 60%, eligible for honors recognition)  

Subject Types  

Core Subject - mandatory subjects (Mathematics, English, Science)  

Elective Subject - optional subjects (Music, Art, Physical Education)  

Console Output Examples  

Screenshot 1: Main Menu  

╔════════════════════════════════════════════╗  
║   STUDENT GRADE MANAGEMENT - MAIN MENU     ║  
╚════════════════════════════════════════════╝  

1. Add Student  
2. View Students  
3. Record Grade  
4. View Grade Report  
5. Exit  

Enter choice: _  

Screenshot 2: View Students  

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

Screenshot 3: Add Student (Regular)  

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

Screenshot 4: Add Student (Honors)  

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

Screenshot 5: Record Grade (Core Subject)  

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

Screenshot 6: Record Grade (Elective Subject)  

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

Screenshot 7: View Grade Report (Empty)  

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

Screenshot 8: View Grade Report (With Records)  

Enter choice: 4  

VIEW GRADE REPORT  
──────────────────────────  

Enter Student ID: STU001  

Student: STU001 - Alice Johnson  
Type: Regular Student  
Current Average: 81.2%  
Status: PASSING ✓  

GRADE HISTORY  
─────────────────────────────────────────────────────────────────────────  
GRD ID  | DATE       | SUBJECT          | TYPE      | GRADE  
─────────────────────────────────────────────────────────────────────────  
GRD001  | 03-11-2025 | Mathematics      | Core      | 85.0%  
GRD002  | 02-11-2025 | English          | Core      | 78.0%  
GRD003  | 01-11-2025 | Science          | Core      | 92.0%  
GRD004  | 31-10-2025 | Music            | Elective  | 88.0%  
GRD005  | 30-10-2025 | Art              | Elective  | 63.0%  
─────────────────────────────────────────────────────────────────────────  

Total Grades: 5  
Core Subjects Average: 85.0%  
Elective Subjects Average: 75.5%  
Overall Average: 81.2%  

Performance Summary:  
✓ Passing all core subjects  
✓ Meeting passing grade requirement (50%)  

Press Enter to continue...  

Screenshot 9: Exit Application  

Enter choice: 5  

Thank you for using Student Grade Management System!  
Goodbye!  

User Stories  

US-1: View Students  

As a teacher  

I want to view all students  

So that I can see their details and performance  

Acceptance Criteria:  

Display minimum 5 students (3 Regular, 2 Honors)  

Show student ID, name, type, average grade, and status  

Regular students show passing grade of 50%  

Honors students show passing grade of 60% and honors eligibility  

Display total students and average class grade  

Classes to Create:  

Student (abstract class)  

Private fields: studentId (String), name (String), age (int), email (String), phone (String), status (String)  

Static field: studentCounter (int)  

Constructor, getters, setters  

Abstract method: displayStudentDetails()  

Abstract method: getStudentType()  

Abstract method: getPassingGrade()  

Method: calculateAverageGrade()  

Method: isPassing()  

RegularStudent extends Student  

Private field: passingGrade = 50.0  

Override methods accordingly  

HonorsStudent extends Student  

Private fields: passingGrade = 60.0, honorsEligible  

Method: checkHonorsEligibility()  

US-2: Add Student  

Capture details, support types, auto ID, confirmation, status Active  

US-3: Record Grade  

Validate student, select subject, validate grade, generate ID  

Classes: Subject, CoreSubject, ElectiveSubject, Gradable, Grade  

US-4: View Grade Report  

Display grades, averages, summary, reverse order  

Class: GradeManager  

US-5: Menu Navigation  

Loop menu, validate input, handle errors  

Class: StudentManager  

Minimum Requirements  

All 9 classes  

All features working  

Arrays used  

Validation implemented  

No errors  

Grading Rubric  

OOP 25  
Functionality 25  
Class Design 15  
Data 15  
Code Quality 10  
Documentation 10  

Testing the Application  

Test Scenario 1: View Students  

Run application  
Select option 2  
Verify 5 students display  
Check passing grades  
Check honors eligibility  
Verify totals  

Test Scenario 2: Add Regular Student  

Select option 1  
Enter details  
Choose Regular  
Verify ID generated  
Verify confirmation  
Verify passing grade  

Test Scenario 3: Add Honors Student  

Select option 1  
Enter details  
Choose Honors  
Verify eligibility  
Verify passing grade  

Test Scenario 4: Record Grade (Core Subject)  

Add student  
Select option 3  
Enter ID  
Select Core  
Choose subject  
Enter grade  
Verify ID  
Confirm  

Test Scenario 5: Record Grade (Elective Subject)  

Select option 3  
Enter ID  
Select Elective  
Choose subject  
Enter grade  
Verify success  

Test Scenario 6: Grade Validation  

Enter invalid grades  
Verify rejection  
Enter valid grade  
Verify acceptance  

Test Scenario 7: View Grade Report (Empty)  

Add student  
View report  
Verify no grades message  

Test Scenario 8: View Grade Report (With Records)  

Add grades  
View report  
Verify display  
Verify averages  
Verify status  

Test Scenario 9: Honors Eligibility Check  

Add honors student  
Add grades >=85  
Verify eligible  
Add grades <85  
Verify change  

Test Scenario 10: Unit Tests Execution  

Run mvn test  
Verify all pass  
Run integration tests  
Verify pass  
Generate jacoco report  
Verify 85%+  
Check performance tests  
Check concurrency  
Review execution  
Document failures  
