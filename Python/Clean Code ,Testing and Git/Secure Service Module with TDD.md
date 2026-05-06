# Secure Service Module with TDD

**Assessment:** Clean Code, Testing & Git  
**Complexity:** Medium  
**Estimated Time:** 6–10 hours

---

## Objectives

By completing this lab, learners should be able to:

- Build a secure, reusable module following a strict TDD process
- Apply SOLID principles to create a decoupled and testable service layer
- Achieve 100% test coverage on the core business logic
- Use modern Python features like type hints and context managers effectively
- Follow a standard Git workflow with code reviews and automated quality checks

---

## Description

Develop a secure, standalone **User Authentication Service Module**. This module will not be a full web application but a reusable library responsible for user registration and credential verification. It must handle password hashing, enforce password policies, and prevent common errors like duplicate registrations.

The entire development process must follow TDD, and the final design must be highly modular and testable, with a goal of 100% code coverage on the core logic.

---

## Implementation Details

### 1. Test-Driven Development (TDD)

- Adhere strictly to the "Red-Green-Refactor" cycle for every feature — commit history should reflect this
- Use `pytest` for testing; the primary goal is 100% statement and branch coverage on the service logic, verified with `coverage.py`
- Use `pytest.raises` to test that custom exceptions are thrown correctly under specific conditions
- Use `pytest-mock` extensively to mock dependencies like the data storage layer

### 2. SOLID Architecture & Code Quality

- Design a `UserService` class as the main entry point for the module
- The service must depend on abstractions (ABCs or Protocols), not concrete implementations — e.g., a `UserRepository` interface and a `PasswordHasher` interface
- Implement concrete versions of these interfaces (e.g., `InMemoryUserRepository`, `BcryptPasswordHasher`)
- This dependency injection pattern is key to making the service testable
- Use `dataclasses` with type hints for user data models; enforce quality with `Black`, `ruff`, and `mypy`

### 3. Error Handling & Security

- Create custom exceptions: `UserAlreadyExistsError`, `InvalidPasswordError`, `UserNotFoundError`
- The `PasswordHasher` implementation must use a strong hashing algorithm like `bcrypt`
- Registration logic should enforce a basic password policy (e.g., minimum length)
- Use structured logging to record significant events like user registration or failed login attempts

### 4. Git & Collaboration Workflow

- Use Git Flow or a similar branching strategy (e.g., `feature/registration`, `feature/login`)
- All new code must be introduced via Pull Requests and undergo a simulated code review
- Set up pre-commit hooks to ensure no low-quality code is ever committed

---

## Milestones

| Day | Focus | Tasks |
|---|---|---|
| Day 1 | TDD Setup & Registration Logic | Set up project, testing tools, and architectural interfaces (`UserRepository`, `PasswordHasher`); write first failing test for user registration; implement registration logic including password hashing; write tests for `UserAlreadyExistsError` |
| Day 2 | Login Logic & Exception Handling | Write failing tests for the login/credential verification process; implement password verification logic; write tests for all failure cases; integrate structured logging for all auth events |
| Day 3 | Refinement & Achieving Full Coverage | Identify untested branches or statements; write tests to bring core service logic to 100% coverage; refactor for clarity; conduct code review on a feature PR |
| Day 4 | Documentation & Finalization | Write comprehensive Google-style docstrings for the entire public API; create `README.md` explaining architecture and usage; perform final check with all quality tools (`mypy`, `ruff`, etc.) |

---

## Grading Criteria (100 Points)

| Criteria | Points | Description |
|---|---|---|
| Feature Implementation | 20 | Authentication module correctly handles registration and login securely |
| Code Quality & Structure | 15 | Flawless execution of SOLID principles, especially dependency injection |
| Best Practices & Patterns | 15 | Strict TDD process followed; strong password hashing and logging |
| Testing & Validation | 20 | 100% test coverage on core logic; excellent use of mocking and `pytest` |
| Documentation & Comments | 10 | Professional-level docstrings and a clear architectural overview in README |
| Final Integration & Output Quality | 20 | The module is a high-quality, reusable, and thoroughly tested library |

---

## Submission Requirements

- Python 3.11+ module
- GitHub repository with a commit history that clearly shows the TDD cycle
- `.pre-commit-config.yaml` and `.gitignore` files
- `requirements.txt` including `bcrypt` and testing tools
- `README.md` explaining the SOLID architecture and providing usage examples
- Final 100% coverage report from `coverage.py`
- Loom video explaining the decoupled architecture and demonstrating how easy it is to test `UserService` because of dependency injection
