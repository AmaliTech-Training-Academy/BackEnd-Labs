# Multi-Stage Data Processing Pipeline

**Assessment:** Clean Code, Testing & Git  
**Complexity:** Medium  
**Estimated Time:** 6–10 hours

---

## Objectives

By completing this lab, learners should be able to:

- Design a modular system using SOLID principles, especially the Single Responsibility Principle
- Write comprehensive unit and integration tests, using `testcontainers-python` for dependencies
- Implement robust error handling and logging for each stage of a pipeline
- Use a standard Git workflow with PRs and pre-commit hooks for quality assurance
- Debug a complex, multi-stage application using IDE debugging tools

---

## Description

Create a data processing pipeline that takes raw text, cleans it, analyzes its sentiment (simulated), and stores the structured result in a real database. Each stage of the pipeline (e.g., cleaner, analyzer, storer) must be a distinct, independently testable component.

This project emphasizes:

- Clean architecture (SOLID)
- Testing pyramid (unit vs. integration tests)
- Observability (logging) in a multi-step process

---

## Implementation Details

### 1. Code Quality & SOLID Architecture

Design separate classes for each stage:

- `TextCleaner`
- `SentimentAnalyzer`
- `DatabaseStorer`

Each class must have a single responsibility. Use ABCs or Protocols to define a common interface for pipeline stages. Use dependency injection to assemble the pipeline and allow stage swapping.

Enforce: `Black`, `ruff`, `mypy`, and full docstrings.

### 2. Testing Pyramid

**Unit Tests:**
- Test each pipeline stage in isolation
- Use `pytest-mock` to mock dependencies

**Integration Tests:**
- Use `testcontainers-python`
- Spin up a PostgreSQL or Redis container
- Feed full pipeline input
- Validate final database output
- Aim for high coverage using `coverage.py`

### 3. Error Handling & Debugging

Each stage must have custom exceptions:
- `CleaningError`
- `AnalysisError`
- `StorageError`

Implement structured logging to:
- Track data as it moves through the pipeline
- Log state after each stage

Intentionally introduce bugs and use:
- Breakpoints
- Watch expressions
- Call stack inspection

### 4. Git Workflow

- Use Git Flow or trunk-based development
- Feature branches per pipeline stage
- Use Pull Requests for review
- Enforce pre-commit hooks

---

## Milestones

| Day | Focus | Tasks |
|---|---|---|
| Day 1 | Architecture, Setup & Unit Tests | Design SOLID pipeline architecture; define interfaces for each stage; set up project, Git, and `testcontainers-python`; write unit tests for `TextCleaner`; implement `TextCleaner` logic |
| Day 2 | Pipeline Stages & Logging | Implement `SentimentAnalyzer` and `DatabaseStorer` following test-first approach; add structured logging across all stages; unit test each stage independently |
| Day 3 | Integration Testing & Debugging | Write integration test using `testcontainers-python`; run full pipeline against real database; introduce intentional bug; debug using IDE tools; document debugging process |
| Day 4 | Refinement & Finalization | Refactor for clarity and performance; ensure all tests pass; achieve coverage targets; write `README.md` with architecture and run instructions |

---

## Grading Criteria (100 Points)

| Criteria | Points | Description |
|---|---|---|
| Feature Implementation | 20 | Pipeline processes data through all stages and stores it correctly |
| Code Quality & Structure | 15 | Strong SOLID design and clean architecture |
| Best Practices & Patterns | 15 | Logging, exceptions, and debugging usage |
| Testing & Validation | 20 | Unit + integration tests using `testcontainers` |
| Documentation & Comments | 10 | Clear README and docstrings |
| Final Integration & Output Quality | 20 | Fully working pipeline with proper Git workflow |

---

## Submission Requirements

- Python 3.11+ application
- GitHub repository with clean commit history
- `.pre-commit-config.yaml` and `.gitignore` files
- `requirements.txt` (including `testcontainers-python`)
- `README.md` with architecture diagram and test instructions
- Test coverage report
- Loom video or screenshots showing debugging session
