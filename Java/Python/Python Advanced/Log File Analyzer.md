# Log File Analyzer with Regex & Functional Programming

**Assessment:** Python Advanced  
**Complexity:** Medium  
**Estimated Time:** 6–10 hours

---

## Objectives

By completing this lab, learners should be able to:

- Master regular expressions using the `re` module (`compile`, `search`, `match`, `findall`, `sub`)
- Apply functional programming patterns (`map`, `filter`, `reduce`)
- Use iterators, generators, and the `yield` statement
- Leverage `itertools` and `functools` for efficient processing
- Implement decorators for function enhancement
- Process large log files efficiently with generators

---

## Description

Create a **Log File Analyzer** that parses web server access logs (Apache/Nginx format), extracts structured information using regex, and generates analytics reports.

You'll use functional programming techniques to filter, transform, and aggregate log entries. Implement decorators for timing, caching, and logging. Use generators to process files line-by-line without loading everything into memory. Apply `itertools` for grouping and windowing operations.

---

## Implementation Details

### 1. Regular Expression Patterns

- Compile regex patterns for common log formats
- Extract: IP addresses, timestamps, HTTP methods, status codes, URLs
- Use named groups for clarity: `(?P<ip>...)`
- Implement validation patterns (email, URL, IP)
- Use `re.sub()` for data cleaning

### 2. Functional Programming

- Use `map()` to transform log lines to structured dictionaries
- Use `filter()` to select specific log entries (status codes, time ranges)
- Use `reduce()` from `functools` for aggregations
- Chain functional operations for readable pipelines

### 3. Generators & Iterators

- Implement generator function to read large files: `yield` each line
- Create custom iterators for batching log entries
- Use `itertools.groupby()` for grouping by status code/hour
- Use `itertools.islice()` for pagination

### 4. Decorators

- `@timer` decorator to measure function execution time
- `@cache` decorator using `functools.lru_cache`
- `@log_call` decorator to trace function calls
- Chain multiple decorators

### 5. itertools & functools Utilities

- Use `itertools.chain()` to combine multiple log files
- Use `itertools.takewhile()` for time-range filtering
- Use `functools.partial()` for creating specialized filter functions

---

## Milestones

| Days | Focus | Tasks |
|---|---|---|
| Day 1–3 | Regex Patterns & Parsing | Define regex patterns for log formats, implement parsing function with named groups, test patterns with sample logs |
| Day 4–5 | Functional Programming Pipeline | Implement `map`/`filter`/`reduce` operations, create functional data transformation pipeline, add `reduce`-based aggregations |
| Day 6–7 | Generators & Decorators | Convert file reading to generator, implement timing and caching decorators, use `itertools` for grouping and windowing |
| Day 8 | Testing & Documentation | Write `pytest` tests for regex patterns, test generator memory efficiency, document functional pipeline design |

---

## Grading Criteria (100 Points)

| Criteria | Points | Description |
|---|---|---|
| Feature Implementation | 20 | Regex parsing, functional transformations, generator-based processing |
| Code Quality & Structure | 15 | Clean functional style, decorator design, generator implementation |
| Best Practices & Patterns | 15 | Proper regex patterns, efficient generators, decorator chaining |
| Testing & Validation | 20 | Regex test suite, functional pipeline tests, generator tests |
| Documentation & Comments | 10 | Regex pattern documentation, functional pipeline explanation |
| Final Integration & Output Quality | 20 | Parsing accuracy, report generation, performance comparison |

---

## Submission Requirements

- Python 3.11+ codebase
- GitHub repo with sample log files (1000+ lines)
- `README.md` with:
  - Regex pattern explanations
  - Functional pipeline visualization
  - Generator vs. list performance comparison
- `pytest` test suite for regex patterns
- Demo showing memory-efficient processing
