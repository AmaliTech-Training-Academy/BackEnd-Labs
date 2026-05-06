# Student Grade Analytics Tool with Advanced Collections

**Assessment:** Python Advanced  
**Complexity:** Medium  
**Estimated Time:** 6–10 hours

---

## Objectives

By completing this lab, learners should be able to:

- Use built-in collections (`Counter`, `defaultdict`, `OrderedDict`, `deque`) for data processing
- Implement `dataclasses` and `namedtuples` for structured data
- Apply type hints for complex structures (`List`, `Dict`, `Optional`, `Union`)
- Understand memory efficiency trade-offs between data structures
- Process CSV and JSON files using context managers
- Generate statistical reports and visualizations

---

## Description

Build a **Student Grade Analytics Tool** that processes student records from CSV files, calculates statistics (averages, distributions, rankings), and generates reports in JSON format.

You'll use advanced collections for efficient data aggregation, `dataclasses` for representing students and courses, and type hints throughout. The tool must handle large datasets efficiently and provide insights like top performers, grade distributions, and trend analysis.

---

## Implementation Details

### 1. Data Structures & Collections

- Use `namedtuple` or `dataclass` for `Student` and `Course` models
- Use `Counter` for grade distribution counting
- Use `defaultdict` for grouping students by major/year
- Use `OrderedDict` for maintaining insertion order in reports
- Use `deque` for implementing a rolling average calculator

### 2. Type Hints & Data Modeling

- Add type hints: `List[Student]`, `Dict[str, List[float]]`, `Optional[Grade]`
- Implement a `TypedDict` for JSON report structure
- Use `Union` types for flexible input handling

### 3. File I/O with Context Managers

- Read CSV files using `with open()` and `csv.DictReader`
- Write JSON reports using `json.dump()`
- Use `pathlib` for file path management
- Handle file not found and permission errors gracefully

### 4. Statistical Processing

- Calculate mean, median, mode using collections
- Compute percentile rankings
- Track grade trends over semesters using `deque`

### 5. Memory Efficiency

- Compare memory usage of different collection approaches
- Use generators for processing large files (bonus)
- Document performance considerations

---

## Milestones

| Days | Focus | Tasks |
|---|---|---|
| Day 1–2 | Data Models & Collections Setup | Define `dataclasses` for `Student`, `Course`, `Grade`; implement collection-based aggregators; add comprehensive type hints |
| Day 3–4 | File Processing | Implement CSV reader with `pathlib`, add JSON report writer, handle file errors with context managers |
| Day 5–6 | Statistical Analysis | Calculate grade distributions with `Counter`, implement ranking algorithm, generate summary reports |
| Day 7 | Testing & Documentation | Write `pytest` tests for each collection type, add docstrings and usage examples, create sample data and README |

---

## Grading Criteria (100 Points)

| Criteria | Points | Description |
|---|---|---|
| Feature Implementation | 20 | Correct use of collections, file I/O, statistical calculations |
| Code Quality & Structure | 15 | Clear organization, PEP 8, proper `dataclass` design |
| Best Practices & Patterns | 15 | Type hints, context managers, error handling |
| Testing & Validation | 20 | `pytest` tests for collections and calculations, sample data tests |
| Documentation & Comments | 10 | Docstrings, type documentation, README with examples |
| Final Integration & Output Quality | 20 | Report accuracy, JSON formatting, performance documentation |

---

## Submission Requirements

- Python 3.11+ codebase
- GitHub repository with sample CSV data
- `requirements.txt` (minimal: `pytest`, `mypy`)
- `README.md` with:
  - Setup instructions
  - Sample input/output
  - Collection performance notes
  - JSON report examples
- Screenshot showing tool execution
