# Student Course Management System

**Topic:** Python Basics  
**Complexity:** Medium  
**Estimated Time:** 6–8 hours

---

## Objectives

By completing this lab, learners should be able to:

- Set up a modern Python environment (Python 3.11+, virtualenv, IDE)
- Work with core data types, operators, and control structures
- Define and use functions effectively (including lambdas and comprehensions)
- Structure reusable modules and packages
- Apply OOP principles: inheritance, polymorphism, encapsulation, and abstract base classes (ABCs)

---

## Description

Build a **Student Course Management System** as a console application. The system should allow:

**Students** to:
- Register
- Enroll in courses
- View summaries

**Instructors** to:
- Manage course rosters
- Track averages

The solution should demonstrate strong use of **Python fundamentals, modular design, and object-oriented programming (OOP)**.

---

## Implementation Details

### 1. Environment Setup

- Install **Python 3.11+**
- Create a virtual environment using `venv`
- Set up an IDE (VS Code or PyCharm)
- Use `requirements.txt` or Poetry for dependency management

### 2. Core Logic and Data Structures

**Use:**
- `Lists` → store collections (students, courses)
- `Dictionaries` → map IDs to objects
- `Sets` → handle unique enrollments

**Apply:**
- List/dict comprehensions for filtering and summaries
- Control flow: `if` statements, `for` / `while` loops, menu-driven CLI logic

### 3. Functions and Modules

Break logic into reusable functions:

- `add_student()`
- `enroll_student()`
- `calculate_average()`

Use `*args`, `**kwargs` for flexibility. Organize into modules:

```
project/
│── main.py
│── student.py
│── course.py
│── enrollment.py
```

### 4. Object-Oriented Design

| Concept | Implementation |
|---|---|
| Classes | `Student`, `Course`, `Enrollment` |
| Encapsulation | Use `@property` for controlled access |
| Inheritance | `GraduateStudent`, `UndergraduateStudent` extend `Student` |
| Abstraction | Use ABCs for report generation |

### 5. Polymorphism and Magic Methods

**Implement:**
- `__repr__()` → readable object output
- `__eq__()` → object comparison

**Demonstrate:**
- Polymorphism in reporting (e.g., different student types)

**Use:**
- `@classmethod`
- `@staticmethod`

---

## Milestones

| Day | Focus | Tasks |
|---|---|---|
| Day 1 | Environment Setup & Data Types | Install Python, create virtualenv, practice data structures |
| Day 2 | Core Functional Logic | Build CLI menu, loops, functions, comprehensions |
| Day 3 | OOP Structure | Create classes, inheritance, encapsulation, polymorphism |
| Day 4 | Packaging & Testing | Refactor modules, test functionality, finalize CLI |

---

## Grading Criteria (100 Points)

| Criteria | Points | Description |
|---|---|---|
| Language Fundamentals | 20 | Proper use of data types, control structures, comprehensions |
| Functions & Modularity | 15 | Reusable, well-structured functions |
| OOP Design Quality | 25 | Proper class design, inheritance, encapsulation |
| Code Clarity & Style | 15 | PEP 8 compliance, readability, naming |
| Documentation & Comments | 10 | Clear docstrings and inline explanations |
| Execution & Output Quality | 15 | Fully working CLI with correct outputs |

---

## Submission Requirements

- Python 3.11+ compatible code
- GitHub repository with clear module structure
- `requirements.txt` or `pyproject.toml`
- `README.md` including setup instructions, usage guide, and example output
- Loom video demo showing:
  - Adding students
  - Enrolling students
  - Generating reports

---

## Outcome

By completing this lab, learners demonstrate the ability to:

- Build a structured Python application
- Apply OOP principles in real scenarios
- Write clean, modular, and maintainable code
- Deliver a functional CLI-based system
