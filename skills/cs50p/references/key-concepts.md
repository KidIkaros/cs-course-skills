# CS50P Key Concepts Cheat Sheet

## Python Fundamentals

### Data Types
```python
int         # Integer: 42, -10, 0
float       # Float: 3.14, -2.5, 1.0
str         # String: "hello", 'world'
bool        # Boolean: True, False
None        # NoneType: None
```

### Variables
```python
x = 10              # Assignment
x: int = 10         # Type hint (optional)
name = "Alice"      # String
pi = 3.14           # Float
is_active = True    # Boolean
```

### Operators
```python
# Arithmetic
+, -, *, /, //, %, **

# Comparison
==, !=, <, >, <=, >=

# Logical
and, or, not

# Assignment
=, +=, -=, *=, /=
```

## Control Flow

### Conditionals
```python
if condition:
    # code
elif other_condition:
    # code
else:
    # code

# Ternary operator
value = x if condition else y
```

### Loops
```python
# While loop
while condition:
    # code

# For loop
for item in iterable:
    # code

# Range
for i in range(10):        # 0 to 9
for i in range(1, 11):     # 1 to 10
for i in range(0, 10, 2):  # 0, 2, 4, 6, 8

# Loop control
break       # Exit loop
continue    # Skip iteration
```

## Functions

### Basic Function
```python
def greet(name):
    return f"Hello, {name}!"

# Function call
message = greet("Alice")
```

### Default Parameters
```python
def greet(name, greeting="Hello"):
    return f"{greeting}, {name}!"
```

### Multiple Returns
```python
def get_coordinates():
    return x, y

x, y = get_coordinates()
```

### Docstrings
```python
def calculate_area(width, height):
    """Calculate the area of a rectangle.
    
    Args:
        width (float): The width
        height (float): The height
    
    Returns:
        float: The area
    """
    return width * height
```

## Data Structures

### Lists
```python
fruits = ["apple", "banana", "cherry"]
fruits.append("date")      # Add to end
fruits.insert(1, "blueberry")  # Insert at index
fruits.remove("banana")    # Remove by value
popped = fruits.pop()      # Remove and return last
fruits.sort()              # Sort in place
length = len(fruits)       # Get length
```

### List Comprehensions
```python
squares = [x**2 for x in range(10)]
evens = [x for x in range(10) if x % 2 == 0]
```

### Dictionaries
```python
person = {"name": "Alice", "age": 30}
person["email"] = "alice@example.com"  # Add
del person["age"]                      # Delete
name = person.get("name", "Unknown")   # Safe get
```

### Dictionary Comprehensions
```python
squares = {x: x**2 for x in range(10)}
```

### Tuples
```python
coordinates = (10, 20)
x, y = coordinates  # Unpacking
```

### Sets
```python
unique_numbers = {1, 2, 3, 4, 5}
unique_numbers.add(6)
unique_numbers.discard(3)
```

## Error Handling

### Try/Except
```python
try:
    result = 10 / 0
except ZeroDivisionError:
    print("Cannot divide by zero")
except Exception as e:
    print(f"Error: {e}")
else:
    print("No error occurred")
finally:
    print("Always executes")
```

### Raising Exceptions
```python
def set_age(age):
    if age < 0:
        raise ValueError("Age cannot be negative")
    return age
```

## File I/O

### Reading Files
```python
with open("file.txt", "r") as file:
    content = file.read()        # Read entire file
    lines = file.readlines()     # Read as list of lines
```

### Writing Files
```python
with open("file.txt", "w") as file:
    file.write("Hello, World!\n")
```

### CSV Files
```python
import csv

# Reading
with open("data.csv", "r") as file:
    reader = csv.reader(file)
    for row in reader:
        print(row)

# Writing
with open("output.csv", "w", newline="") as file:
    writer = csv.writer(file)
    writer.writerow(["Name", "Age"])
    writer.writerow(["Alice", 30])
```

### JSON Files
```python
import json

# Reading
with open("data.json", "r") as file:
    data = json.load(file)

# Writing
with open("output.json", "w") as file:
    json.dump(data, file, indent=2)
```

## Regular Expressions

### Basic Patterns
```python
import re

# Search
match = re.search(r"pattern", string)

# Find all
matches = re.findall(r"pattern", string)

# Substitute
result = re.sub(r"pattern", "replacement", string)
```

### Common Patterns
```python
r"\d"      # Digit
r"\w"      # Word character
r"\s"      # Whitespace
r"^"       # Start of string
r"$"       # End of string
r"*"       # Zero or more
r"+"       # One or more
r"?"       # Zero or one
r"{n}"     # Exactly n times
r"{n,m}"   # n to m times
r"()"      # Group
```

### Email Validation
```python
pattern = r"^[\w\.-]+@[\w\.-]+\.\w+$"
is_valid = bool(re.match(pattern, email))
```

## Object-Oriented Programming

### Class Definition
```python
class Person:
    def __init__(self, name, age):
        self.name = name
        self.age = age
    
    def greet(self):
        return f"Hello, I'm {self.name}"
```

### Inheritance
```python
class Student(Person):
    def __init__(self, name, age, grade):
        super().__init__(name, age)
        self.grade = grade
    
    def study(self):
        return f"{self.name} is studying"
```

### Special Methods
```python
class Vector:
    def __init__(self, x, y):
        self.x = x
        self.y = y
    
    def __repr__(self):
        return f"Vector({self.x}, {self.y})"
    
    def __add__(self, other):
        return Vector(self.x + other.x, self.y + other.y)
```

## Unit Testing

### pytest Basics
```python
# test_example.py
def test_addition():
    assert 1 + 1 == 2

def test_string():
    assert "hello".upper() == "HELLO"
```

### Testing Exceptions
```python
import pytest

def test_zero_division():
    with pytest.raises(ZeroDivisionError):
        1 / 0
```

### Running Tests
```bash
pytest                    # Run all tests
pytest test_file.py       # Run specific file
pytest -v                 # Verbose output
pytest -x                 # Stop on first failure
```

## Common Functions

### Built-in Functions
```python
len(x)          # Length
type(x)         # Type
int(x)          # Convert to int
float(x)        # Convert to float
str(x)          # Convert to string
bool(x)         # Convert to bool
list(x)         # Convert to list
dict(x)         # Convert to dict
sorted(x)       # Return sorted list
reversed(x)     # Return reversed iterator
enumerate(x)    # Return index-value pairs
zip(x, y)       # Combine iterables
map(func, x)    # Apply function
filter(func, x) # Filter elements
```

### String Methods
```python
str.upper()         # Convert to uppercase
str.lower()         # Convert to lowercase
str.strip()         # Remove whitespace
str.split()         # Split into list
str.join()          # Join list to string
str.replace()       # Replace substring
str.find()          # Find substring index
str.startswith()    # Check prefix
str.endswith()      # Check suffix
str.isdigit()       # Check if digits
str.isalpha()       # Check if letters
```

### List Methods
```python
list.append(x)      # Add to end
list.insert(i, x)   # Insert at index
list.remove(x)      # Remove by value
list.pop()          # Remove and return last
list.sort()         # Sort in place
list.reverse()      # Reverse in place
list.index(x)       # Find index of value
list.count(x)       # Count occurrences
```

## Best Practices

1. **Use meaningful variable names**
2. **Write docstrings for functions**
3. **Handle exceptions gracefully**
4. **Use context managers for files**
5. **Write unit tests**
6. **Follow PEP 8 style guide**
7. **Use type hints for clarity**
8. **Keep functions small and focused**
9. **Avoid global variables**
10. **Comment complex logic**