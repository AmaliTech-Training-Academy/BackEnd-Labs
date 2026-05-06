# Employee Payroll Tracker

**Assessment Topic:** Python Basics
**Complexity:** Medium
**Estimated Time:** 6–8 hours

---

## Objectives

By completing this lab, learners should be able to:

- Practice numerical operations, loops, and conditionals
- Implement modular functions for salary computation
- Demonstrate inheritance and polymorphism through employee roles
- Use property decorators (`@property`) for data validation
- Apply debugging techniques and virtual environments

---

## Description

Develop an **Employee Payroll Tracker** that computes payslips for multiple employee categories, such as:

- Full-time employees
- Contract employees
- Interns

This lab focuses on applying:

- Python operators and data structures
- Modular programming
- Object-Oriented Programming (OOP) concepts such as inheritance, encapsulation, and polymorphism

---

## Implementation Details

### 1. Setup

- Create a Python virtual environment (`venv`)
- Configure package management (`requirements.txt` or Poetry)
- Use an IDE (VS Code or PyCharm) for development and debugging

### 2. Core Python Concepts

**Use:**
- `Lists` → store employee records
- `Dictionaries` → map employee IDs to payroll data

**Apply:**
- Arithmetic operations for salary calculations
- Conditional logic (`if/else`) for role-based rules
- Loops (`for`, `while`) for processing multiple employees

### 3. Functions and Modules

Implement reusable functions such as:

- `calculate_salary()`
- `apply_tax()`
- `generate_payslip()`

Organize code into modules:

```
project/
│── main.py
│── employee.py
│── payroll.py
│── utils.py
```

### 4. Object-Oriented Design

| Concept | Implementation |
|---|---|
| Base Class | `Employee` |
| Subclasses | `FullTimeEmployee`, `ContractEmployee`, `Intern` |
| Inheritance | Subclasses extend base class behavior |
| Encapsulation | Protect payroll data using private attributes |
| Method Override | Each role overrides salary calculation logic |

### 5. Properties & Data Validation

Use `@property` for:

- Salary
- Bonus
- Tax

Ensure:

- Valid ranges (e.g., `salary > 0`)
- Controlled updates to sensitive data

### 6. Polymorphism

Implement role-based salary calculations:

- Same method (`calculate_salary()`) behaves differently per employee type
- Generate reports dynamically based on employee role

---

## Milestones

| Day | Focus | Tasks |
|---|---|---|
| Day 1 | Environment Setup | Setup Python, virtualenv, define data structures |
| Day 2 | Functions & Logic | Implement salary calculations and helper functions |
| Day 3 | OOP Structure | Create classes, inheritance, and property decorators |
| Day 4 | Testing & Debugging | Package modules, test application, debug issues |

---

## Grading Criteria (100 Points)

| Criteria | Points | Description |
|---|---|---|
| Language Fundamentals | 20 | Correct use of data types, control structures, comprehensions |
| Functions & Modularity | 15 | Well-structured and reusable functions |
| OOP Design Quality | 25 | Proper class hierarchy, encapsulation, inheritance |
| Code Clarity & Style | 15 | PEP 8 compliance, readability, naming conventions |
| Documentation & Comments | 10 | Clear docstrings and inline explanations |
| Execution & Output Quality | 15 | Fully functional and stable CLI output |

---

## Submission Requirements

Follow the same structure as Lab 1 submission.

Include:

- Python 3.11+ compatible code
- GitHub repository with clear module structure
- `requirements.txt` or `pyproject.toml`
- `README.md` (setup, usage, sample output)

> **Additional Requirement:** Include screenshots or a short video demonstrating debugging in your IDE.

---

## Outcome

By completing this lab, learners will:

- Strengthen their understanding of Python fundamentals
- Apply OOP concepts in real-world payroll systems
- Build modular, maintainable applications
- Demonstrate debugging and problem-solving skills
