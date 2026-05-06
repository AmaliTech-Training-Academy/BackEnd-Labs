# Git-Powered Configuration Management CLI

**Assessment:** Clean Code, Testing & Git  
**Complexity:** Medium  
**Estimated Time:** 6–10 hours

---

## Objectives

By completing this lab, learners should be able to:

- Master Git workflows by building a tool that interacts with a Git repository programmatically
- Handle merge conflicts and different branching strategies within the tool
- Apply SOLID principles to separate Git logic from configuration parsing
- Write tests for a Git-dependent application using temporary repositories
- Implement robust exception handling, logging, and code quality checks

---

## Description

Create a CLI tool that uses a Git repository as a versioned backend for application configurations. Each version of a configuration file (e.g., a JSON or YAML file) will be a commit. The tool will provide commands to create, update, and rollback configurations, using Git branches and commits to manage the history.

This lab provides a deep, practical dive into Git automation and collaboration patterns.

---

## Implementation Details

### 1. Git Automation & Workflow

- Use the `GitPython` library to perform Git operations (`init`, `clone`, `add`, `commit`, `branch`, `merge`) from within Python code
- Implement a branching strategy: allow users to create "draft" configurations on feature branches and then "publish" them by merging into `main`
- Programmatically handle and report merge conflicts, guiding the user on how to resolve them
- Manage a clean `.gitignore` file within the configuration repository the tool controls

### 2. Code Quality & SOLID Design

- Separate concerns: create a `GitRepository` class for all Git interactions and a `ConfigParser` class for reading/writing configuration files (JSON/YAML)
- The main CLI logic should depend on abstractions of these components
- Enforce strict code quality with `Black`, `ruff`, `mypy`, and pre-commit hooks
- Provide clear Google-style docstrings for the public API of all modules

### 3. Error Handling & Logging

- Define custom exceptions: `ConfigNotFound`, `MergeConflictError`, `InvalidRepoError`
- Implement structured logging to provide an audit trail of every action performed by the tool
- Use context managers to handle temporary clones or file checkouts safely

### 4. Testing a Git-Based Application

- Write `pytest` fixtures that create temporary, empty Git repositories before each test runs
- Tests will use the tool's logic to interact with these temporary repos and assert that the Git state (commits, branches, file content) is correct
- Use mocking to test failure scenarios without performing actual Git operations (e.g., simulating a failed push)
- Ensure high test coverage with `coverage.py`

---

## Milestones

| Day | Focus | Tasks |
|---|---|---|
| Day 1 | Setup & Core Git Interaction | Set up project, CLI framework (`click` or `argparse`), and `GitPython`; create a `pytest` fixture to manage temporary Git repos; implement core functions for initializing and reading from a configuration repository |
| Day 2 | Feature Implementation & Branching | Implement logic for creating and updating configurations using feature branches; develop the "publish" command that merges a feature branch into `main`; add robust exception handling for common Git and file errors |
| Day 3 | Merge Conflicts & Advanced Testing | Implement functionality to detect and report merge conflicts; write tests that intentionally create merge conflict scenarios; add structured logging to all operations |
| Day 4 | Refinement, Documentation & Final Review | Refactor code to improve structure and SOLID adherence; write comprehensive `README.md` explaining tool commands and Git workflow; ensure all tests pass and pre-commit hooks are clean |

---

## Grading Criteria (100 Points)

| Criteria | Points | Description |
|---|---|---|
| Feature Implementation | 20 | CLI tool correctly manages configurations using Git branches and commits |
| Code Quality & Structure | 15 | Clean separation between Git logic and configuration parsing; adherence to SOLID |
| Best Practices & Patterns | 15 | Robust handling of Git states, merge conflicts, and exceptions |
| Testing & Validation | 20 | Effective testing strategy using temporary Git repos; high test coverage |
| Documentation & Comments | 10 | Clear README with command examples and workflow explanation |
| Final Integration & Output Quality | 20 | The tool is robust, and the Git workflow is well-designed and implemented |

---

## Submission Requirements

- Python 3.11+ CLI application
- GitHub repository with a clean commit history
- `.pre-commit-config.yaml` and `.gitignore` files
- `requirements.txt` including `GitPython`
- `README.md` with detailed instructions and examples for each command
- A test coverage report
- Loom video demonstrating the CLI tool's full lifecycle: creating a draft config, publishing it, updating it, and handling a merge conflict
