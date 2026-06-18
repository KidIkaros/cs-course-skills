# CS50x Key Concepts Cheat Sheet

## Computational Thinking
- **Decomposition**: Breaking problems into smaller parts
- **Pattern Recognition**: Finding similarities across problems
- **Abstraction**: Hiding implementation details
- **Algorithms**: Step-by-step instructions

## C Language Fundamentals

### Data Types
```c
int i = 42;           // Integer (4 bytes)
float f = 3.14;       // Floating point (4 bytes)
double d = 3.14159;   // Double precision (8 bytes)
char c = 'A';         // Character (1 byte)
bool b = true;        // Boolean (from stdbool.h)
```

### Operators
```c
// Arithmetic: +, -, *, /, %
// Comparison: ==, !=, <, >, <=, >=
// Logical: && (and), || (or), ! (not)
// Assignment: =, +=, -=, *=, /=
```

### Conditionals
```c
if (condition) {
    // code
} else if (condition) {
    // code
} else {
    // code
}

// Ternary operator
int max = (a > b) ? a : b;
```

### Loops
```c
// for loop
for (int i = 0; i < n; i++) {
    // code
}

// while loop
while (condition) {
    // code
}

// do-while loop
do {
    // code
} while (condition);
```

### Functions
```c
// Declaration
int add(int a, int b);

// Definition
int add(int a, int b) {
    return a + b;
}

// Void function
void printHello(void) {
    printf("Hello\n");
}
```

## Memory and Pointers

### Pointer Basics
```c
int x = 42;
int *p = &x;      // p stores address of x
printf("%d\n", *p); // Dereference: prints 42
*p = 100;          // x is now 100
```

### Dynamic Memory
```c
#include <stdlib.h>

// Allocate memory
int *arr = malloc(n * sizeof(int));

// Check for NULL
if (arr == NULL) {
    return 1;
}

// Use memory
arr[0] = 42;

// Free memory
free(arr);
arr = NULL; // Good practice
```

### Memory Layout
```
┌─────────────────┐ High address
│      Stack      │ ← Local variables, function calls
├─────────────────┤
│        ↓        │
│                 │
│        ↑        │
├─────────────────┤
│       Heap      │ ← malloc, dynamic allocation
├─────────────────┤
│       BSS       │ ← Uninitialized globals
├─────────────────┤
│      Data       │ ← Initialized globals
├─────────────────┤
│      Text       │ ← Program code
└─────────────────┘ Low address
```

## Data Structures

### Arrays
```c
int arr[5] = {1, 2, 3, 4, 5};
// Access: arr[index]
// Time: O(1) access, O(n) search
```

### Linked Lists
```c
typedef struct node {
    int number;
    struct node *next;
} node;

// Insert at beginning
node *new = malloc(sizeof(node));
new->number = 1;
new->next = list;
list = new;
```

### Hash Tables
```c
// Hash function maps keys to indices
unsigned int hash(const char *word) {
    int sum = 0;
    for (int i = 0; word[i]; i++) {
        sum += word[i];
    }
    return sum % TABLE_SIZE;
}
```

### Tries
```c
typedef struct node {
    struct node *children[26];
    bool is_word;
} node;
```

## Python Basics

### Data Structures
```python
# Lists (mutable)
lst = [1, 2, 3]
lst.append(4)
lst[0]  # 1

# Tuples (immutable)
tup = (1, 2, 3)

# Dictionaries
d = {"key": "value"}
d["new_key"] = 42

# Sets
s = {1, 2, 3}
s.add(4)
```

### Functions
```python
def greet(name):
    return f"Hello, {name}!"

# Lambda
add = lambda a, b: a + b
```

### List Comprehensions
```python
squares = [x**2 for x in range(10)]
evens = [x for x in range(10) if x % 2 == 0]
```

## SQL

### CRUD Operations
```sql
-- Create
INSERT INTO users (name, email) VALUES ('Alice', 'alice@example.com');

-- Read
SELECT * FROM users WHERE name = 'Alice';
SELECT name, COUNT(*) FROM users GROUP BY name;

-- Update
UPDATE users SET email = 'new@example.com' WHERE id = 1;

-- Delete
DELETE FROM users WHERE id = 1;
```

### Joins
```sql
-- INNER JOIN
SELECT * FROM users JOIN orders ON users.id = orders.user_id;

-- LEFT JOIN
SELECT * FROM users LEFT JOIN orders ON users.id = orders.user_id;
```

## Web Development

### HTML Structure
```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>
    <h1>Heading</h1>
    <p>Paragraph</p>
</body>
</html>
```

### CSS Selectors
```css
/* Element */
p { color: blue; }

/* Class */
.highlight { background: yellow; }

/* ID */
#header { font-size: 2em; }

/* Descendant */
div p { margin: 10px; }
```

### JavaScript Basics
```javascript
// Variables
let x = 5;
const PI = 3.14;

// Functions
function greet(name) {
    return `Hello, ${name}`;
}

// Arrow functions
const add = (a, b) => a + b;

// DOM
document.querySelector("#id").addEventListener("click", handler);
```

### Flask Routes
```python
from flask import Flask, render_template, request

app = Flask(__name__)

@app.route("/")
def index():
    return render_template("index.html")

@app.route("/submit", methods=["POST"])
def submit():
    name = request.form.get("name")
    return f"Hello, {name}"
```

## Algorithm Analysis

### Big O Notation
| Complexity | Name | Example |
|-----------|------|---------|
| O(1) | Constant | Array access |
| O(log n) | Logarithmic | Binary search |
| O(n) | Linear | Linear search |
| O(n log n) | Linearithmic | Merge sort |
| O(n²) | Quadratic | Bubble sort |
| O(2ⁿ) | Exponential | Recursive Fibonacci |

### Sorting Algorithms
| Algorithm | Best | Average | Worst | Space |
|-----------|------|---------|-------|-------|
| Selection Sort | n² | n² | n² | 1 |
| Bubble Sort | n | n² | n² | 1 |
| Merge Sort | n log n | n log n | n log n | n |

## Security

### Password Hashing
```python
# Using bcrypt
import bcrypt
hashed = bcrypt.hashpw(password.encode(), bcrypt.gensalt())
```

### SQL Injection Prevention
```python
# Use parameterized queries
cursor.execute("SELECT * FROM users WHERE id = ?", (user_id,))

# NEVER do this
# cursor.execute(f"SELECT * FROM users WHERE id = {user_id}")
```
