Task Management System  
Project Overview  

Complexity: Medium  
Time Estimate: 6–8 hours  
Technology Stack: Java 21 (LTS), IntelliJ IDEA Community Edition, JUnit 5  

This lab builds Lab 1 – Java Basics by refactoring the Project/Task Management System for cleaner, safer, and testable code.  

You’ll apply exception handling, SOLID principles, and unit testing using JUnit 5, while maintaining version control with Git.  

All functionality from Lab 1 (Project creation, Task management, Completion averages) remains, but now enhanced with:  

Custom exceptions for invalid inputs  
Refactored, modular code with better naming and organization  
Basic JUnit tests for core functions  
Git repository setup and proper commit workflow  

All data remains in memory using arrays (no external DB). Future labs will introduce collections and file persistence.  

Project Objectives  

By completing this lab, you will be able to:  

Apply clean code principles (SOLID, naming conventions, method modularity).  
Implement exception handling using try-catch blocks and custom exceptions.  
Refactor Lab 1 code for improved readability and maintainability.  
Write and run JUnit unit tests for methods like task status updates and completion calculations.  
Use Git for source control: initialize repositories, commit changes, create branches, and merge.  
Evaluate code quality through consistent indentation, comments, and naming.  
Handle invalid user inputs gracefully through custom exception messages.  
Prepare the system for future enhancements (Week 3 will replace arrays with collections).  

System Features Overview  

Your Project/Task Management System should now include error handling, refactoring, and testing enhancements for these five core features:  

Feature 1: Project Catalog Management  

Same as Lab 1 (creating and listing projects).  
Add validation via custom exceptions (e.g., InvalidProjectDataException).  
Enforce unique project IDs and positive budgets.  

Feature 2: Task Operations  

Handle invalid task assignments gracefully (throw TaskNotFoundException).  
Refactor task creation/update methods for clarity.  
Add unit tests for task status updates and progress calculation.  

Feature 3: User Management  

Refactor user logic to separate responsibilities (e.g., UserService).  
Validate email and role inputs through exceptions.  
Use Git branches for adding new user roles (clean commit history).  

Feature 4: Status Processing & Reporting  

Add validation for projects with no tasks (throw EmptyProjectException).  
Test average calculation methods via JUnit.  
Refactor printing logic to utility methods.  

Feature 5: Menu Navigation & User Experience  

Improve input validation with exception handling.  
Display user-friendly error messages for invalid entries.  
Ensure menu loops remain stable under exceptions.  

Console UI Examples  

Below are sample enhanced console outputs showing error handling and testing feedback.  

1. Main Menu  

╔════════════════════════════════════════════╗  
║     JAVA PROJECT MANAGEMENT SYSTEM         ║  
╚════════════════════════════════════════════╝  

Current User:  Alice Johnson (Admin)  

Main Menu:  
-----------  
1. Manage Projects  
2. Manage Tasks  
3. View Status Reports  
4. Switch User  
5. Exit  

Enter your choice: _  

2. Invalid Input Handled via Exception  

Enter project ID: P999  
❌ Error: ProjectNotFoundException – Project ID 'P999' does not exist.  
Please try again.  

Enter project ID: P001  
✓ Project 'Alpha Tracker' loaded successfully.  

3. Add Task – Validation  

╔════════════════════════════════════════════╗  
║               ADD NEW TASK                 ║  
╚════════════════════════════════════════════╝  

Enter task name: Implement API  
Enter status (Pending/In Progress/Completed): In Progress  

✓ Task 'Implement API' successfully added to Project P001.  

4. Exception During Task Update  

Enter task ID: T999  
❌ Error: TaskNotFoundException – Task 'T999' was not found in the project.  

Operation aborted. Returning to task menu...  

5. Status Report Display  

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

6. Git Commit Workflow (Example Output)  

git init  
git add .  
git commit -m "Refactor: Added custom exceptions and cleaned class structure"  
git branch feature/testing  
git checkout feature/testing  
git add src/test  
git commit -m "Test: Added JUnit test for progress calculation"  
git checkout main  
git merge feature/testing  

7. JUnit Test Example  

@Test  
void testCalculateCompletionPercentage() {  
   Project p = new SoftwareProject("P001", "Alpha Tracker", 5, 15000);  
   p.addTask(new Task("T001", "Setup DB", "Completed"));  
   p.addTask(new Task("T002", "Design UI", "In Progress"));  

   double result = p.calculateCompletionPercentage();  
   assertEquals(50.0, result);  
}  

Expected User Workflows  

Workflow 1: Refactor and Run  

User opens existing Lab 1 project → Refactors code → Runs updated program → Confirms all previous features still work.  

Workflow 2: Exception Handling  

User enters invalid data (e.g., negative budget) → System throws custom exception → Displays error → Returns to menu without crashing.  

Workflow 3: Unit Testing  

User writes JUnit tests for calculateCompletionPercentage() → Runs tests → All pass with green indicators.  

Workflow 4: Git Versioning  

User initializes Git repo → Makes commits after refactoring and testing → Creates branch for new exceptions → Merges cleanly.  

User Stories  

Epic 1: Code Refactoring  

US-1.1: Refactor Class Design As a developer I want to simplify methods and names so that the code is easier to maintain.  

Acceptance Criteria:  

No duplicate logic.  
Descriptive method and variable names.  
Single Responsibility per class.  

Technical Requirements:  

Apply SOLID principles (Single Responsibility, Open/Closed).  
Split large methods into smaller ones.  
Use meaningful naming and comments.  

Epic 2: Exception Handling  

US-2.1: Handle Invalid Inputs As a system I want to catch invalid user inputs so that the program does not crash.  

Acceptance Criteria:  

Throws custom exceptions (e.g., InvalidInputException, TaskNotFoundException).  
Displays clear error messages.  
Logs errors to console gracefully.  

Technical Requirements:  

Use try-catch-finally blocks.  
Create custom exception classes in utils.exceptions.  
Handle validation centrally via ValidationUtils.  

Epic 3: Testing Fundamentals  

US-3.1: Test Completion Calculation As a developer I want to verify that completion percentages are accurate.  

Acceptance Criteria:  

At least 3 JUnit tests for different cases (no tasks, partial, all completed).  
All tests pass successfully.  

Technical Requirements:  

Add src/test/java/ directory.  
Use JUnit 5 annotations (@Test, @BeforeEach).  
Assertions: assertEquals, assertThrows.  

Epic 4: Git Version Control  

US-4.1: Version Code Changes As a developer I want to track changes and refactors using Git so that my code history is maintained.  

Acceptance Criteria:  

Repository initialized and linked to GitHub.  
Minimum 3 meaningful commits.  
One feature branch created and merged.  

Technical Requirements:  

Run git init, git add ., git commit.  
Use branches (e.g., feature/exceptions).  
Merge via git merge.  

Epic 5: Menu Error Handling  

US-5.1: Handle Menu Errors As a user I want the menu to remain functional after invalid inputs.  

Acceptance Criteria:  

Program does not crash on invalid entry.  
Error message and retry prompt displayed.  

Technical Requirements:  

Use input validation and try-catch in ConsoleMenu.  
Implement looping until valid entry is provided.  

Project Structure  

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

Implementation Phases  

Phase 1: Refactor Existing Code (1–2 hours)  

Tasks:  

Review Lab 1 code.  
Apply SOLID and naming best practices.  
Separate concerns into services and utils.  

Deliverables: Refactored, readable code with consistent structure.  

Phase 2: Add Exception Handling (2 hours)  

Tasks:  

Create custom exception classes.  
Add try-catch logic around input operations.  

Deliverables: Program handles invalid inputs gracefully without crashing.  

Phase 3: JUnit Testing (2 hours)  

Tasks:  

Write unit tests for key methods.  
Run tests in IntelliJ using JUnit 5.  

Deliverables: All tests passing; test coverage for critical logic.  

Phase 4: Git Version Control (1–2 hours)  

Tasks:  

Initialize Git repository.  
Commit changes incrementally.  
Push to GitHub and create branches for features.  

Deliverables: Organized commit history with proper branch merging.  

Minimum Requirements Checklist  

JDK 21 and IntelliJ IDEA installed and configured  
Refactored code from Lab 1 with clean structure  
At least 3 custom exception classes implemented  
All exceptions properly handled via try-catch  
At least 3 JUnit test cases passing successfully  
Meaningful variable and method names used throughout  
Methods follow Single Responsibility Principle  
Git repository initialized and hosted on GitHub  
At least 3 commits with clear messages  
Feature branch created and merged successfully  
Console menu remains functional after errors  
README updated with refactoring and Git instructions  
All previous Lab 1 features remain functional  

Grading Rubric  

Criteria | Points  
Code Refactoring & Clean Code | 20  
Exception Handling | 20  
Testing & Coverage | 20  
Git Version Control | 15  
Functionality & Stability | 15  
Data Structures & Algorithms (DSA) | 10  
Total | 100  

Submission Requirements  

Required Deliverables:  

Public GitHub Repository containing:  
All source code (/src, /test)  
README.md with setup and Git instructions  
JUnit test results screenshot (optional)  

Documentation must include:  

Setup and run instructions  
Feature summary mapped to user stories  
Class diagram and refactoring explanation  
Commit log snapshot showing version control usage  

Submission Link:  

Please fill out this form (insert actual form link here)  

Testing the Application  

Test Scenario 1: Refactored Project Creation  

Run the refactored application  
Select option 1 (Add Project)  
Enter valid details for a Software Project  
Verify constructors and encapsulation work correctly (no direct field access)  
Confirm ID auto-generates (e.g., PRJ001)  
Check logs or console output for clean, formatted messages  

Test Scenario 2: Add Task with Exception Handling  

Select option 3 (Add Task)  
Enter invalid project ID (e.g., PRJ999)  
Verify custom exception displays user-friendly error message  
Enter valid project ID and task details  
Confirm successful task creation and no unhandled exceptions  

Test Scenario 3: View Projects (After Refactoring)  

Select option 2 (View Projects)  
Verify that the refactored structure (using classes and encapsulation) displays data neatly  
Check tasks associated with each project load properly  
Confirm no redundant or duplicate display entries  

Test Scenario 4: Calculate Completion Percentage (Refactored Logic)  

Select option 6 (Calculate Project Completion)  
Enter valid Project ID  
Verify accurate completion percentage after code refactoring  
Check that calculations are performed in a dedicated method/class  
Confirm clear and readable output formatting  

Test Scenario 5: Exception Handling for Invalid Inputs  

Enter invalid options (letters for numeric input, negative hours, etc.)  
Verify input validation prevents crashes  
Confirm appropriate custom exceptions or fallback messages display  
Check that retry prompts appear correctly  

Test Scenario 6: Run JUnit Tests  

Open the JUnit test class in the IDE  
Run test methods for Project creation, Task addition, and completion calculation  
Verify all tests pass successfully  
Confirm proper assertions (e.g., expected vs actual completion %)  
Check test coverage summary  

Test Scenario 7: Git Commit and Branch Workflow  

Initialize Git repository if not done  
Make initial commit for the refactored code  
Create new branch “feature/task-validation”  
Add validation updates and commit  
Merge back into main branch without conflicts  
Verify commit history shows meaningful messages  

Test Scenario 8: Git Push and Remote Verification  

Push changes to remote repository (e.g., GitHub)  
Confirm commits reflect online with correct timestamps  
Verify README and .gitignore files are included  
Check that teammates can clone and run project successfully  

Test Scenario 9: Code Cleanliness and Comments Check  

Open-source files (Project.java, Task.java, Main.java)  
Verify consistent indentation and naming conventions  
Confirm presence of JavaDoc comments on methods  
Check for absence of dead code or unused imports  
