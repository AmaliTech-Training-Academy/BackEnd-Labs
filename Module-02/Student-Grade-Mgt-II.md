# Student Grade Management System

## Project Overview

**Complexity:** Medium
**Time Estimate:** 10 hours
**Technology Stack:** Java 21 (LTS), IntelliJ IDEA Community Edition

Build a console-based Project/Task Management System where users can create projects, add and assign tasks, record task completion status, and calculate completion averages.

This lab focuses on core Java programming and object-oriented principles while storing all data in-memory using arrays (no databases or external dependencies).

This project forms the foundation for a progressive multi-week Project Management system.

---

## Learning Objectives

By completing this lab, you will be able to:

* Design console-based Java applications
* Apply OOP principles (encapsulation, inheritance, polymorphism)
* Use arrays, loops, and conditionals for in-memory data handling
* Implement abstract classes and interfaces
* Demonstrate method overloading and overriding
* Build menu-driven applications with validation
* Compute completion percentages from task data

---

## System Features Overview

| Feature                    | Description                                |
| -------------------------- | ------------------------------------------ |
| Project Catalog Management | Create and view software/hardware projects |
| Task Operations            | Add, update, delete, and view tasks        |
| User Management            | Admin and Regular users with roles         |
| Status Reporting           | Completion percentages and summaries       |
| Menu Navigation            | Console-based system navigation            |

---

## Console UI Examples

### Main Menu

```
JAVA PROJECT MANAGEMENT SYSTEM
Current User: Alice Johnson (Admin)

1. Manage Projects
2. Manage Tasks
3. View Reports
4. Switch User
5. Exit
```

---

### Project Catalog

| ID   | Name           | Type     | Team Size | Budget  |
| ---- | -------------- | -------- | --------- | ------- |
| P001 | Alpha Tracker  | Software | 5         | $15,000 |
| P002 | IoT Sensor Kit | Hardware | 3         | $10,000 |

---

### Project Details

| Task ID | Task Name       | Status      |
| ------- | --------------- | ----------- |
| T001    | Design Database | Completed   |
| T002    | API Development | In Progress |
| T003    | Unit Tests      | Pending     |

Completion Rate: **33%**

---

### Status Report

| Project ID | Name           | Tasks | Completed | Progress |
| ---------- | -------------- | ----- | --------- | -------- |
| P001       | Alpha Tracker  | 4     | 3         | 75%      |
| P002       | IoT Sensor Kit | 2     | 1         | 50%      |

**Average Completion: 62.5%**

---

## Input Validation Examples

| Input                 | Error Message                        |
| --------------------- | ------------------------------------ |
| XYZ (invalid ID)      | Invalid input. Use P001 format       |
| Done (invalid status) | Choose Pending/In Progress/Completed |
| -3 team size          | Must be greater than 0               |

---

## User Stories

### Project Management

* View projects
* Filter by type
* Search by budget

### Task Management

* Add tasks
* Update status
* Delete tasks

### User Roles

* Admin (full access)
* Regular (limited access)

### Reporting

* Completion percentage per project

### Navigation

* Menu-driven system
* Loop until exit

---

## Project Structure

```
src/
├── Main.java
├── models/
│   ├── Project.java
│   ├── SoftwareProject.java
│   ├── HardwareProject.java
│   ├── Task.java
│   ├── User.java
│   ├── AdminUser.java
│   ├── RegularUser.java
│   └── StatusReport.java
├── interfaces/
│   └── Completable.java
├── services/
│   ├── ProjectService.java
│   ├── TaskService.java
│   └── ReportService.java
├── utils/
│   ├── ConsoleMenu.java
│   └── ValidationUtils.java
```

---

## Implementation Phases

| Phase   | Duration | Tasks                |
| ------- | -------- | -------------------- |
| Phase 1 | 1–2 hrs  | Setup + base classes |
| Phase 2 | 2–3 hrs  | Core logic + tasks   |
| Phase 3 | 2–3 hrs  | UI + menus           |
| Phase 4 | 1 hr     | Documentation        |

---

## Requirements Checklist

| Requirement      | Status   |
| ---------------- | -------- |
| JDK 21 setup     | Required |
| Abstract classes | Required |
| Interfaces       | Required |
| Arrays usage     | Required |
| Encapsulation    | Required |
| Validation       | Required |
| Polymorphism     | Required |

---

## Testing Scenarios

### Project Creation

* Verify ID generation
* Verify storage in array

### Task Management

* Add task
* Update task
* Delete task

### Reporting

* Validate completion %

### Input Handling

* Invalid menu selection
* Non-numeric input handling

### ID Generation

* Ensure uniqueness (PRJ001, TSK001)

---

## Grading Rubric

| Criteria       | Weight | Excellent (90–100%)                         | Good (75–89%)         | Satisfactory (60–74%) |
| -------------- | ------ | ------------------------------------------- | --------------------- | --------------------- |
| OOP Principles | 25     | Full abstraction, inheritance, polymorphism | Minor design issues   | Basic usage only      |
| Functionality  | 25     | All features working                        | Most features working | Partial functionality |
| Class Design   | 15     | Proper relationships                        | Minor issues          | Incomplete structure  |
| DSA Usage      | 15     | Efficient array logic                       | Moderate efficiency   | Basic implementation  |
| Code Quality   | 10     | Clean, validated                            | Mostly clean          | Needs improvement     |
| Documentation  | 10     | Full README + UML                           | Partial docs          | Minimal docs          |

---

## Submission Requirements

* GitHub repository
* README.md
* UML diagram
* Design explanation

---
