# Task Management System

Task Management System  

Project Overview  

Technology Stack: Java 21 (LTS), IntelliJ IDEA Community Edition  

Build a console-based Project/Task Management System where users can create projects, add and assign tasks, record task completion status, and calculate completion averages.  

This lab focuses on core Java programming and object-oriented principles while storing all data in-memory using arrays (no databases or external dependencies).  

The lab serves as the foundation for the multi-week Project Management series.  

Future labs will gradually enhance this base — replacing arrays with collections, adding file persistence, and integrating user authentication and reporting dashboards.  

Project Objectives  

By completing this lab, you will be able to:  

Understand how to design a simple console-based application using core Java.  

Apply object-oriented programming principles (encapsulation, inheritance, and polymorphism) to represent projects, tasks, and users.  

Use Java arrays, loops, and conditional structures to manage and manipulate data in memory.  

Define and extend classes, abstract classes, and interfaces to promote clean, reusable designs.  

Demonstrate method overloading and method overriding to implement flexible and polymorphic behaviors.  

Design simple menu-driven console interfaces with structured user input validation.  

Compute project completion percentages by aggregating data from arrays of task statuses.  

Lay the groundwork for future enhancements, where arrays will evolve into Java Collections and file-based data storage.  

System Features Overview  

Your Project/Task Management System should support the following five core features:  

Feature 1: Project Catalog Management  

Create new projects (e.g., SoftwareProject, HardwareProject).  

View all existing projects with details (ID, name, description, team size, budget, etc.).  

Filter projects by type (software/hardware).  

Display project-specific attributes dynamically.  

Feature 2: Task Operations  

Add tasks to specific projects.  

Assign task status (Pending, In Progress, Completed).  

View all tasks per project with progress details.  

Update or delete tasks.  

Validate inputs to prevent invalid task status or duplicate task names.  

Feature 3: User Management  

Create and manage system users (RegularUser and AdminUser).  

Assign users to projects or tasks.  

Enforce role-based access (Admin can delete/update; Regular can view/add).  

Automatically generate unique user IDs.  

Feature 4: Status Processing & Reporting  

Calculate and display completion averages per project.  

Generate status reports (e.g., “Project Alpha is 75% complete”).  

Display task statistics: total, completed, and pending counts.  

Show per-user performance summaries (future expansion).  

Feature 5: Menu Navigation & User Experience  

Display a clear main menu and sub-menus for operations.  

Validate all user inputs (numbers, text, IDs).  

Provide formatted outputs with clear sections and alignment.  

Support graceful exit and return navigation.  

Console UI Examples  

1. Main Menu  

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

2. Project Catalog Display  

╔════════════════════════════════════════════╗  
║               PROJECT CATALOG              ║  
╚════════════════════════════════════════════╝  

Filter Options:  
1. View All Projects (5)  
2. Software Projects Only  
3. Hardware Projects Only  
4. Search by Budget Range  

Enter filter choice: 1  

─────────────────────────────────────────────────────────────────────  
ID   | PROJECT NAME         | TYPE       | TEAM SIZE | BUDGET  
─────────────────────────────────────────────────────────────────────  
P001 | Alpha Tracker        | Software   | 5         | $15,000  
     | Description: Task tracking app for startups  
─────────────────────────────────────────────────────────────────────  
P002 | IoT Sensor Kit       | Hardware   | 3         | $10,000  
     | Description: Sensor prototype for smart devices  
─────────────────────────────────────────────────────────────────────  

Enter project ID to view details (or 0 to return): _  

3. Project Details View  

╔════════════════════════════════════════════╗  
║           PROJECT DETAILS: P001            ║  
╚════════════════════════════════════════════╝  

Project Name: Alpha Tracker  
Type: Software  
Team Size: 5  
Budget: $15,000  

Associated Tasks:  
─────────────────────────────────────────────────────────────────────  
ID   | TASK NAME          | STATUS  
─────────────────────────────────────────────────────────────────────  
T001 | Design Database    | Completed  
T002 | Implement API      | In Progress  
T003 | Write Unit Tests   | Pending  
─────────────────────────────────────────────────────────────────────  

Completion Rate: 33%  

Options:  
1. Add New Task  
2. Update Task Status  
3. Remove Task  
4. Back to Main Menu  

Enter your choice: _  

4. Add Task  

╔════════════════════════════════════════════╗  
║               ADD NEW TASK                 ║  
╚════════════════════════════════════════════╝  

Enter task name: Implement UI  
Enter assigned project ID: P001  
Enter initial status (Pending/In Progress/Completed): Pending  

✓ Task "Implement UI" added successfully to Project P001!  

5. Update Task Status  

Enter task ID: T002  
Enter new status: Completed  

✓ Task "Implement API" marked as Completed.  

6. Status Report Display  

╔════════════════════════════════════════════╗  
║            PROJECT STATUS REPORT           ║  
╚════════════════════════════════════════════╝  

─────────────────────────────────────────────────────────────────────  
PROJECT ID | PROJECT NAME      | TASKS | COMPLETED | PROGRESS (%)  
─────────────────────────────────────────────────────────────────────  
P001       | Alpha Tracker     |   4   |    3      |   75%  
P002       | IoT Sensor Kit    |   2   |    1      |   50%  
─────────────────────────────────────────────────────────────────────  

AVERAGE COMPLETION: 62.5%  

7. Input Validation Examples  

Enter project ID: XYZ  
❌ Error: Invalid input. Please enter a valid numeric or prefixed ID (e.g., P001).  

Enter task status: Done  
❌ Error: Invalid status. Please choose from [Pending, In Progress, Completed].  

Enter team size: -3  
❌ Error: Team size must be greater than 0.  

Enter again: 5  
✓ Project successfully created.  

Expected User Workflows  

Workflow 1: Complete Task Assignment Journey  

User logs into system.  
System displays the main menu.  
User selects “Manage Projects.”  
User adds a new project (“Alpha Tracker”).  
User adds tasks under that project.  
User updates task statuses.  
System calculates completion average.  
User views report.  

Workflow 2: Project Discovery  

User selects “Browse Projects.”  
Filters by Software Projects.  
Views detailed project info.  
Adds a new related task.  
Returns to main menu.  

Workflow 3: Task Management  

User opens “Manage Tasks.”  
Views tasks for selected project.  
Updates task status.  
Deletes outdated tasks.  
System recalculates progress.  

Workflow 4: Status Reporting  

User opens “View Status Reports.”  
System displays all projects with completion percentages.  
User compares project progress and returns to menu.  

User Stories  

Epic 1: Project Catalog Management  

US-1.1: Browse Projects  

As a user  

I want to view all available projects with their details  

So that I can understand ongoing work.  

Acceptance Criteria:  

Display all projects with ID, name, type, and budget.  
Show team size and description.  
Support filtering by project type.  

Technical Requirements:  

Create abstract class Project with private fields id, name, description, budget, teamSize, abstract method getProjectDetails(), and concrete method displayProject().  
Implement subclasses SoftwareProject and HardwareProject.  
Store projects in an array (minimum 5).  

US-1.2: Search Projects by Budget Range  

As a user  

I want to search projects within a specified budget range  

So that I can filter based on funding.  

Acceptance Criteria:  

Input min and max budget.  
Show projects within range or “No projects found.”  
Validate numeric inputs.  

Technical Requirements:  

Use comparison operators and loops.  
Use conditionals to check valid range.  
Display formatted output using System.out.printf().  

Epic 2: Task Operations  

US-2.1: Add Task to Project  

As a user  

I want to add tasks under a project  

So that I can track progress effectively.  

Acceptance Criteria:  

Assign unique task IDs.  
Specify task name and initial status.  
Prevent duplicates.  

Technical Requirements:  

Create Task class with fields id, name, status.  
Implement interface Completable with method boolean isCompleted().  
Store tasks in an array within each project.  

US-2.2: Update Task Status  

As a user  

I want to update the status of a task  

So that progress reflects accurately.  

Acceptance Criteria:  

Select task by ID.  
Choose from allowed statuses.  
Update and display success message.  

Technical Requirements:  

Use loops to locate task.  
Use enums/constants.  
Apply encapsulation.  

Epic 3: User Management  

US-3.1: Create User Profiles  

As a system  

I want to create different user roles  

So that permissions can vary.  

Acceptance Criteria:  

Create RegularUser and AdminUser.  
Assign auto IDs.  
Display role.  

Technical Requirements:  

Abstract User class with fields id, name, email, role.  
Use static counter.  
Apply inheritance and polymorphism.  

Epic 4: Status Processing & Reporting  

US-4.1: Calculate Project Completion Average  

As a system  

I want to calculate how many tasks are completed  

Acceptance Criteria:  

Display totals and percentage.  
Handle zero tasks.  
Round to 2 decimals.  

Technical Requirements:  

Use loops and arithmetic.  

Epic 5: Menu Navigation  

US-5.1: Display Main Menu  

As a user  

I want to navigate easily  

Acceptance Criteria:  

Menu 1–5  
Validate input  
Loop until exit  

Technical Requirements:  

Scanner + switch + do-while  

Testing the Application  

Test Scenario 1: View Projects  

Run application  
Select option 2  
Verify projects display correctly  
Verify separation  
Verify totals  
Verify array usage  

Test Scenario 2: Add Software Project  

Select option 1  
Enter details  
Verify ID  
Verify storage  

Test Scenario 3: Add Hardware Project  

Repeat and verify type + ID  

Test Scenario 4: Add Task  

Select option 3  
Enter project  
Enter task  
Verify storage  

Test Scenario 5: View Tasks  

Select option 4  
Verify display  
Check empty case  

Test Scenario 6: Update Task Status  

Select option 5  
Update  
Verify change  

Test Scenario 7: Calculate Completion Percentage  

Select option 6  
Verify %  
Test edge cases  

Test Scenario 8: Handle Invalid Inputs  

Enter invalid inputs  
Verify messages  
Ensure no crash  

Test Scenario 9: ID Auto-generation  

Create multiple entries  
Verify sequential IDs  
Ensure uniqueness  
