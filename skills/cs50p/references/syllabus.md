# CS50P Syllabus - Weekly Breakdown

## Week 0: Functions, Variables

**Topics:**
- Installing Python and VS Code
- Writing your first program
- Functions and arguments
- Variables and types
- Integer arithmetic
- Type conversion
- Conditionals (if/elif/else)

**Key Concepts:**
- `print()` function
- Variable assignment
- Data types (int, float, str, bool)
- Type conversion with `int()`, `float()`, `str()`
- Basic conditional statements

**Practice:**
- Write a "Hello, World" program
- Create a tip calculator
- Build a simple calculator

---

## Week 1: Conditionals

**Topics:**
- Boolean expressions
- Logical operators (and, or, not)
- Comparison operators
- Nested conditionals
- Ternary operators

**Key Concepts:**
- Comparison operators: `==`, `!=`, `<`, `>`, `<=`, `>=`
- Logical operators: `and`, `or`, `not`
- Truthy and falsy values
- Nested if statements

**Practice:**
- Grade calculator
- Rock, Paper, Scissors game
- Eligibility checker

---

## Week 2: Loops

**Topics:**
- `while` loops
- `for` loops
- `range()` function
- Loop control (break, continue)
- Nested loops

**Key Concepts:**
- `while condition:` loop
- `for variable in iterable:` loop
- `range(start, stop, step)`
- `break` and `continue` statements
- Loop patterns and common use cases

**Practice:**
- Number guessing game
- Print patterns with nested loops
- Find factors of a number

---

## Week 3: Exceptions

**Topics:**
- `try`/`except` blocks
- Multiple except clauses
- Raising exceptions
- Common exception types
- Clean error handling

**Key Concepts:**
- `try:` / `except:` blocks
- `except ExceptionType:` specific catching
- `raise ValueError("message")`
- Common exceptions: `ValueError`, `TypeError`, `ZeroDivisionError`, `FileNotFoundError`
- `else` and `finally` clauses

**Practice:**
- Input validation with error handling
- Division calculator with zero-check
- File reading with error handling

---

## Week 4: Libraries

**Topics:**
- Importing modules
- `from...import` syntax
- Common standard library modules
- `math`, `random`, `statistics`
- Third-party packages

**Key Concepts:**
- `import module_name`
- `from module_name import function`
- `import module_name as alias`
- Standard library: `math`, `random`, `statistics`, `sys`, `os`
- Installing packages with `pip`

**Practice:**
- Generate random passwords
- Calculate statistical measures
- Create a coin flip simulator

---

## Week 5: Unit Tests

**Topics:**
- `pytest` framework
- Writing test functions
- Assertions
- Running tests
- Test-driven development

**Key Concepts:**
- Test functions start with `test_`
- `assert` statements
- `pytest.raises` for exception testing
- Running tests with `pytest` command
- Test organization and naming

**Practice:**
- Write tests for a calculator function
- Test string manipulation functions
- Create a test suite for a library

---

## Week 6: File I/O

**Topics:**
- Reading files
- Writing files
- Context managers (`with` statement)
- CSV processing
- JSON handling

**Key Concepts:**
- `open(filename, mode)` function
- File modes: `'r'`, `'w'`, `'a'`, `'r+'`
- `with open(...) as file:` context manager
- `file.read()`, `file.readline()`, `file.readlines()`
- `csv.reader()`, `csv.writer()`
- `json.load()`, `json.dump()`

**Practice:**
- Read and process a text file
- Write data to a CSV file
- Create a JSON data store

---

## Week 7: Regular Expressions

**Topics:**
- `re` module
- Pattern matching
- Quantifiers and anchors
- Groups and capturing
- Common patterns

**Key Concepts:**
- `re.search(pattern, string)`
- `re.findall(pattern, string)`
- `re.sub(pattern, replacement, string)`
- Quantifiers: `*`, `+`, `?`, `{n}`, `{n,m}`
- Anchors: `^`, `$`
- Character classes: `\d`, `\w`, `\s`
- Groups: `()`

**Practice:**
- Validate email addresses
- Extract phone numbers from text
- Parse log files

---

## Week 8: Object-Oriented Programming

**Topics:**
- Classes and objects
- Attributes and methods
- `__init__` constructor
- `self` parameter
- Inheritance
- Polymorphism

**Key Concepts:**
- `class ClassName:`
- `def __init__(self, ...):`
- Instance methods: `def method(self):`
- Instance variables: `self.variable = value`
- Class variables
- Inheritance: `class Child(Parent):`
- Method overriding

**Practice:**
- Create a BankAccount class
- Build a Deck of Cards
- Design a Student grade system

---

## Week 9: Advanced Topics

**Topics:**
- Decorators
- Generators
- Lambda functions
- List comprehensions
- Dictionary comprehensions

**Key Concepts:**
- Decorators: `@decorator` syntax
- Generators: `yield` keyword
- Lambda: `lambda x: expression`
- List comprehensions: `[x for x in iterable]`
- Dictionary comprehensions: `{k: v for k, v in iterable}`
- `map()`, `filter()`, `reduce()`

**Practice:**
- Create a caching decorator
- Build a number generator
- Transform data with comprehensions