# Library Inventory Application

**Topic:** Python Basics  
**Complexity:** Medium  
**Estimated Time:** 6–8 hours

---

## Objectives

By completing this lab, learners should be able to:

- Apply functions, loops, and file I/O operations
- Organize code into modules and packages effectively
- Use classes and Abstract Base Classes (ABCs) for structured design
- Implement comprehensions for searching and categorizing data
- Use special methods like `__repr__`, `__eq__`, and `super()` effectively

---

## Description

Develop a **Library Inventory Application** to manage:

- Books
- Authors
- Borrowers

The system should allow users to:

- Add and manage books
- Search and filter inventory
- Track borrowed items
- Generate reports

The application should emphasize **clean OOP design, modular structure, and maintainable code**.

---

## Implementation Details

### 1. File Handling (Persistence)

Use Python file I/O to store and retrieve data:

- JSON (recommended) or text files

Persist:
- Book records
- Borrowing history

### 2. Core Data Structures

**Use:**
- `Lists` → store collections of books and borrowers
- `Dictionaries` → map IDs to objects

**Apply comprehensions for:**
- Searching books by title/author
- Filtering available vs borrowed items

### 3. Functions and Modules

Implement reusable functions:

- `add_book()`
- `search_books()`
- `borrow_book()`
- `return_book()`

Suggested project structure:

```
project/
│── main.py
│── book.py
│── author.py
│── borrower.py
│── utils.py
│── data/
    └── library.json
```

### 4. Object-Oriented Design

| Concept | Implementation |
|---|---|
| Base Class (ABC) | `LibraryResource` |
| Classes | `Book`, `Author`, `Borrower` |
| Inheritance | `EBook`, `AudioBook` extend `Book` |
| Encapsulation | Use private attributes with getters/setters |
| Abstraction | Define common interface in ABC |

### 5. Advanced OOP Features

**Use:**
- `__repr__()` → readable object display
- `__eq__()` → object comparison
- `super()` → reuse parent class logic

**Ensure:**
- Clean inheritance structure
- Reusable methods across subclasses

### 6. Reporting & Comprehensions

Generate reports such as:
- Available books
- Borrowed books
- Books by author

Use list/dict comprehensions for efficient filtering and categorization.

---

## Milestones

| Day | Focus | Tasks |
|---|---|---|
| Day 1 | Setup & Data Structures | Setup environment, define data storage and structures |
| Day 2 | Functional Logic | Implement add/search/borrow functions |
| Day 3 | OOP Design | Create classes, inheritance, and ABC structure |
| Day 4 | Packaging & Testing | Organize modules, test application, document code |

---

## Grading Criteria (100 Points)

Same as Lab 1 & Lab 2.

| Criteria | Points | Description |
|---|---|---|
| Language Fundamentals | 20 | Data types, loops, comprehensions |
| Functions & Modularity | 15 | Reusable, well-structured functions |
| OOP Design Quality | 25 | Proper class hierarchy and abstraction |
| Code Clarity & Style | 15 | Readability, naming, PEP 8 |
| Documentation & Comments | 10 | Clear explanations and docstrings |
| Execution & Output Quality | 15 | Fully working and stable CLI |

---

## Submission Requirements

Follow the same structure as Lab 1 & Lab 2:

- Python 3.11+ compatible code
- GitHub repository with clean module structure
- `requirements.txt` or `pyproject.toml`
- `README.md` including setup instructions, usage guide, and example outputs

---

## Outcome

By completing this lab, learners will:

- Build a file-based Python application
- Apply OOP concepts in a real-world inventory system
- Practice data persistence and structured design
- Improve code organization and maintainability
