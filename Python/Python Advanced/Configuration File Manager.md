# Configuration File Manager with Path & Format Handling

**Assessment:** Python Advanced  
**Complexity:** Medium  
**Estimated Time:** 6–10 hours

---

## Objectives

By completing this lab, learners should be able to:

- Use `pathlib` for modern, cross-platform path handling
- Read/write CSV, JSON, and XML formats with context managers
- Apply type hints with `TypedDict` and `Protocol`
- Use generators for memory-efficient file processing
- Implement iterators for custom file traversal
- Apply functional programming for data transformation

---

## Description

Create a **Configuration File Manager** that reads configuration from multiple formats (JSON, CSV, XML), validates structure, converts between formats, and manages config file versions.

Use `pathlib` for all file operations. Implement generators for reading large config files. Use `TypedDict` for config schema validation. Apply functional programming for transformation pipelines. This lab focuses on practical file I/O and data format handling.

---

## Implementation Details

### 1. pathlib for Path Management

- Use `Path` objects instead of string paths
- Implement file discovery: `Path.glob()`, `Path.rglob()`
- Check file existence, permissions, modification times
- Create directories with `Path.mkdir(parents=True)`

### 2. Multi-Format Support

- Read/write JSON with schema validation
- Parse CSV with `csv.DictReader` / `DictWriter`
- Parse XML with `xml.etree.ElementTree`
- Convert between formats maintaining structure

### 3. Type Hints & Validation

- Define `TypedDict` for config schemas
- Use `Protocol` for format handler interface
- Type hint all I/O operations
- Validate configs against schemas

### 4. Generators for Large Files

- Implement generator to read CSV line-by-line
- Use `yield` to parse XML elements incrementally
- Compare memory usage: generator vs. loading full file

### 5. Functional Transformation Pipeline

- Use `map()` to transform config entries
- Use `filter()` to select valid configs
- Chain operations for format conversion

### 6. Context Managers

- All file operations use `with` statement
- Create custom context manager for config transactions
- Ensure proper file handle cleanup

---

## Milestones

| Days | Focus | Tasks |
|---|---|---|
| Day 1–2 | pathlib & Basic I/O | Implement `pathlib`-based file operations, add JSON reader/writer with context managers, implement file discovery |
| Day 3–4 | Multi-Format Support | Add CSV parser, add XML parser, implement format conversion |
| Day 5–6 | Type Hints & Validation | Define `TypedDict` schemas, add validation logic, implement `Protocol` for handlers |
| Day 7 | Generators & Testing | Convert readers to generators, write `pytest` tests for each format, document memory efficiency gains |

---

## Grading Criteria (100 Points)

| Criteria | Points | Description |
|---|---|---|
| Feature Implementation | 20 | All format parsers working, conversion accurate |
| Code Quality & Structure | 15 | Clean `pathlib` usage, proper context managers |
| Best Practices & Patterns | 15 | Type hints with `TypedDict`, generator efficiency, `Protocol` design |
| Testing & Validation | 20 | Tests for each format, validation tests, generator tests |
| Documentation & Comments | 10 | Format documentation, schema definitions, usage examples |
| Final Integration & Output Quality | 20 | Conversion accuracy, file handling robustness |

---

## Submission Requirements

- Python 3.11+ codebase
- GitHub repo with sample config files (JSON, CSV, XML)
- `README.md` with:
  - Format support matrix
  - Schema definitions
  - Conversion examples
- `pytest` test suite
- Memory usage comparison report
