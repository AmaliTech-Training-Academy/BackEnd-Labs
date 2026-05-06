# TDD-Based API Service Stub

**Assessment:** Clean Code, Testing & Git  
**Complexity:** Medium  
**Estimated Time:** 6–10 hours

---

## Objectives

By completing this lab, learners should be able to:

- Apply a strict Test-Driven Development (TDD) workflow to build a service
- Master `pytest` features like fixtures, parametrization, and mocking
- Implement clean, type-hinted code that adheres to SOLID principles
- Use a trunk-based development workflow with pull requests and code reviews
- Integrate structured logging and custom exceptions for a production-ready module

---

## Description

Build a mock "Weather API" service module following a rigorous TDD methodology. The service will not connect to a real external API but will simulate one, returning predictable data for known inputs and specific errors for invalid ones.

Every piece of logic must be preceded by a failing test. The project emphasizes the "Red-Green-Refactor" TDD cycle, high test coverage, and clean, decoupled architecture using SOLID principles.

---

## Implementation Details

### 1. Testing First (TDD)

- Follow the TDD cycle: write a failing test (**Red**), write the minimum code to pass the test (**Green**), then refactor (**Refactor**)
- Use `pytest` for all tests; create fixtures for setting up the service client
- Heavily use `pytest-mock` to simulate dependencies like external APIs or databases from the very beginning
- The final code must have near 100% test coverage, validated by `coverage.py`

### 2. Core Logic & Error Handling

- Create a `WeatherService` class that exposes methods like `get_forecast(city: str)`
- Define custom exceptions like `InvalidAPIKeyError` and `CityNotFoundError`
- Implement structured logging to trace incoming requests and service responses
- The service should return consistent, predefined data for a set of known cities

### 3. Code Quality & Structure

- Use `dataclasses` with strict type hints for request parameters and response models
- Apply SOLID principles: `WeatherService` should depend on an abstract `WeatherProvider` interface, allowing easy swapping of the mock provider for a real one later
- Use `Black` for formatting and `ruff`/`pylint` for linting, enforced by pre-commit hooks
- Write comprehensive Google-style docstrings for all classes and methods

### 4. Git Workflow & Collaboration

- Use a trunk-based development workflow: create short-lived feature branches from `main`
- All code must be merged into `main` through Pull Requests that require a simulated peer review
- Resolve any merge conflicts that arise during the process
- Configure `.gitignore` and pre-commit hooks for code quality checks

---

## Milestones

| Day | Focus | Tasks |
|---|---|---|
| Day 1 | TDD Setup & First Feature | Set up project, Git repo, and testing tools; write the first failing test for `get_forecast`; implement minimum code to pass; set up pre-commit hooks and PR workflow |
| Day 2 | Handling Edge Cases & Errors | Write failing tests for invalid inputs; implement exception handling logic; refactor error handling and integrate structured logging |
| Day 3 | Architectural Refinement (SOLID) | Write tests requiring a more flexible architecture; refactor service to use dependency injection and ABCs; conduct code review on the architectural PR |
| Day 4 | Finalization, Coverage & Documentation | Add remaining tests to achieve near 100% coverage; write final `README.md`; complete all docstrings and type hints; ensure `mypy` passes in strict mode |

---

## Grading Criteria (100 Points)

| Criteria | Points | Description |
|---|---|---|
| Feature Implementation | 20 | Mock service correctly handles all specified valid and invalid scenarios |
| Code Quality & Structure | 15 | Excellent adherence to SOLID principles, type hints, and clean design |
| Best Practices & Patterns | 15 | TDD workflow evident in commit history; proper use of logging and exceptions |
| Testing & Validation | 20 | Near 100% test coverage; effective use of `pytest`, fixtures, and mocking |
| Documentation & Comments | 10 | Clear docstrings and a README that explains the TDD approach |
| Final Integration & Output Quality | 20 | Clean Git history, passing pre-commit hooks, well-structured project |

---

## Submission Requirements

- Python 3.11+ application
- GitHub repository with a commit history clearly demonstrating the TDD cycle
- `.pre-commit-config.yaml` and `.gitignore` files
- `requirements.txt` with all dependencies
- `README.md` explaining the TDD process and final architecture
- A high-coverage test report from `coverage.py`
- Loom video explaining the TDD workflow by showing a few Red-Green-Refactor cycles from the commit history
