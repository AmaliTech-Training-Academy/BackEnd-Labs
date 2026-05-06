# Resilient Data Importer CLI

**Assessment:** Clean Code, Testing & Git  
**Complexity:** Medium  
**Estimated Time:** 6–10 hours

---

## Objectives

By completing this lab, learners should be able to:

- Implement robust exception handling with custom exception classes and context managers
- Apply code quality best practices including PEP 8, type hints, and SOLID principles
- Use a standard Git workflow (Git Flow) with pull requests and pre-commit hooks
- Write a comprehensive test suite with `pytest`, including mocking and achieving high test coverage

---

## Description

Build a command-line interface (CLI) tool that reliably imports user data from a CSV file into a simulated database (a JSON file). The tool must be resilient to errors such as missing files, malformed CSV rows, and duplicate user entries.

You will define custom exceptions to handle these specific error cases gracefully. The implementation must adhere to strict code quality standards, be managed under a Git Flow branching strategy, and be validated by a thorough test suite using `pytest`.

---

## Implementation Details

### 1. Core Logic & Error Handling

- Implement a parser for CSV files that reads user data (e.g., `user_id`, `name`, `email`)
- Define a custom exception hierarchy (e.g., `ImporterError`, `FileFormatError`, `DuplicateUserError`)
- Use `try/except/else/finally` blocks to handle I/O and data validation errors
- Implement a context manager (`with` statement) for safe file reading and writing
- Configure structured logging with Python's `logging` module to report successes, warnings, and errors during the import process

### 2. Code Quality & Structure

- Adhere strictly to PEP 8, enforced by formatters like `Black`
- Use type hints for all function signatures and variables, and validate with `mypy`
- Apply SOLID principles: create separate components for data parsing, validation, and storage (the "repository" pattern)
- Use `dataclasses` or simple classes for structured data representation (e.g., a `User` class)
- Write clear, Google-style docstrings for all modules and public functions

### 3. Git Workflow & Collaboration

- Initialize a Git repository and use the Git Flow branching strategy (`main`, `develop`, feature branches like `feature/csv-parser`)
- Create and manage a `.gitignore` file suitable for a Python project
- Implement a pull request (PR) workflow for merging features into the `develop` branch
- Configure pre-commit hooks to automatically run `Black`, `ruff`, and `mypy` before each commit

### 4. Testing & Validation

- Use `pytest` as the testing framework
- Create fixtures to provide temporary CSV files and mock database objects for tests
- Use `pytest.mark.parametrize` to test the parser with various valid and invalid data inputs
- Mock the file system and storage layer using `pytest-mock` to isolate components during unit testing
- Aim for and report on >90% test coverage using `coverage.py`

---

## Milestones

| Day | Focus | Tasks |
|---|---|---|
| Day 1 | Setup, Design & Git Workflow | Initialize project structure, Git repository, and virtual environment; set up pre-commit hooks; design main classes and custom exception hierarchy; implement basic CLI entry point and file reading logic |
| Day 2 | Core Feature Implementation & Error Handling | Develop CSV parser and data validation logic; implement custom exception handling for all error cases; integrate structured logging |
| Day 3 | Comprehensive Testing | Write unit tests for parser, validator, and storage components; use mocking to isolate units; write integration tests for end-to-end import process; achieve and document target coverage |
| Day 4 | Refinement, Documentation & Final Review | Refactor code based on linting feedback; complete all docstrings; write `README.md`; conduct final code review via PR merge |

---

## Grading Criteria (100 Points)

| Criteria | Points | Description |
|---|---|---|
| Feature Implementation | 20 | CLI tool correctly imports data and handles all specified errors |
| Code Quality & Structure | 15 | Adherence to PEP 8, type hints, SOLID principles, and clear structure |
| Best Practices & Patterns | 15 | Proper exception handling, context managers, logging, and pre-commit hooks |
| Testing & Validation | 20 | High-quality `pytest` suite with >90% coverage, effective use of mocking |
| Documentation & Comments | 10 | Comprehensive docstrings, clear `README.md`, and inline comments |
| Final Integration & Output Quality | 20 | Git workflow correctly followed, clean commit history, functional tool |

---

## Submission Requirements

- Python 3.11+ application
- GitHub repository with a clear commit history showing the Git Flow process
- `.pre-commit-config.yaml` and `.gitignore` files
- `requirements.txt` listing all dependencies
- `README.md` with detailed setup and execution instructions
- A test coverage report (HTML or text format)
- Loom video demonstrating the CLI tool handling both successful imports and various errors
