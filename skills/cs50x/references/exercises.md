# CS50x Practice Exercises

## Week 0 - Scratch
### Exercise 0.1: Hello World
**Difficulty**: Easy
Create a Scratch project that displays "Hello, World!" when the green flag is clicked.

### Exercise 0.2: Personal Greeting
**Difficulty**: Easy
Create a Scratch project that asks the user for their name and says "Hello, [name]!"

### Exercise 0.3: Animation
**Difficulty**: Medium
Create a Scratch project with a character that moves across the screen, bounces off edges, and changes costume to animate.

### Exercise 0.4: Calculator
**Difficulty**: Medium
Create a Scratch calculator that asks for two numbers and an operation (+, -, *, /) and displays the result.

---

## Week 1 - C
### Exercise 1.1: Mario Pyramid
**Difficulty**: Easy
```c
// Print a right-aligned pyramid of height n
// Input: 4
// Output:
//    #
//   ##
//  ###
// ####
```

### Exercise 1.2: Credit Card Validator
**Difficulty**: Medium
```c
// Implement Luhn's algorithm to validate credit card numbers
// Input: 4003600000000014
// Output: VISA (or INVALID)
```

### Exercise 1.3: Temperature Converter
**Difficulty**: Easy
```c
// Convert Fahrenheit to Celsius: C = (F - 32) × 5/9
// Input: 100
// Output: 37.78
```

### Exercise 1.4: Collatz Conjecture
**Difficulty**: Medium
```c
// Count steps to reach 1: if even, divide by 2; if odd, multiply by 3 and add 1
// Input: 27
// Output: 111 steps
```

---

## Week 2 - Arrays
### Exercise 2.1: Readability Score
**Difficulty**: Medium
```c
// Implement Coleman-Liau index to grade text readability
// Input: "Congratulations! Today is your day."
// Output: Grade 3
```

### Exercise 2.2: Substitution Cipher
**Difficulty**: Medium
```c
// Encrypt text using a substitution cipher
// Input: "HELLO" with key "YTNSHKVEFXRBAUQZCLWMGJDOP"
// Output: "EQBBY"
```

### Exercise 2.3: Caesar Cipher
**Difficulty**: Easy
```c
// Encrypt text using Caesar cipher (shift by key)
// Input: "HELLO" with key 3
// Output: "KHOOR"
```

### Exercise 2.4: Array Search
**Difficulty**: Easy
```c
// Implement linear search and binary search
// Test with sorted and unsorted arrays
```

---

## Week 3 - Algorithms
### Exercise 3.1: Sorting Comparison
**Difficulty**: Medium
```c
// Implement selection sort, bubble sort, and merge sort
// Compare execution time for different input sizes
```

### Exercise 3.2: Recursive Fibonacci
**Difficulty**: Easy
```c
// Implement Fibonacci using recursion
// Then optimize with memoization
// Input: 10
// Output: 55
```

### Exercise 3.3: Runoff Voting
**Difficulty**: Hard
```c
// Implement instant-runoff voting system
// Handle voter preferences and eliminate candidates
```

### Exercise 3.4: Merge Sort Implementation
**Difficulty**: Medium
```c
// Implement merge sort from scratch
// Test with array of 1000 random integers
```

---

## Week 4 - Memory
### Exercise 4.1: Filter (Image Processing)
**Difficulty**: Hard
```c
// Apply image filters: grayscale, reflect, blur, edge detection
// Work with BMP file format
```

### Exercise 4.2: Recover Deleted Images
**Difficulty**: Medium
```c
// Recover JPEG images from memory card dump
// Identify file headers and extract data
```

### Exercise 4.3: Pointer Practice
**Difficulty**: Easy
```c
// Write functions that use pointers:
// - swap(int *a, int *b)
// - string_length(char *s)
// - string_copy(char *dst, char *src)
```

### Exercise 4.4: Dynamic Array
**Difficulty**: Medium
```c
// Implement a dynamic array that grows as elements are added
// Use malloc and realloc
```

---

## Week 5 - Data Structures
### Exercise 5.1: Speller
**Difficulty**: Hard
```c
// Implement a spell-checker using a hash table
// Load dictionary, check words, report misspellings
```

### Exercise 5.2: Linked List Operations
**Difficulty**: Medium
```c
// Implement linked list with:
// - Insert at beginning/end
// - Delete by value
// - Search
// - Print all elements
```

### Exercise 5.3: Hash Table Implementation
**Difficulty**: Medium
```c
// Implement a hash table with chaining
// Test with 1000 random keys
```

### Exercise 5.4: Trie Implementation
**Difficulty**: Hard
```c
// Implement a trie for dictionary lookup
// Test with sample dictionary
```

---

## Week 6 - Python
### Exercise 6.1: Mario (Python Version)
**Difficulty**: Easy
```python
# Reimplement Mario pyramid in Python
# Use input validation
```

### Exercise 6.2: DNA Analysis
**Difficulty**: Medium
```python
# Read DNA sequence and count STR repeats
# Match against database of individuals
```

### Exercise 6.3: Regular Expressions
**Difficulty**: Medium
```python
# Validate email addresses using regex
# Test cases: valid and invalid emails
```

### Exercise 6.4: File Processing
**Difficulty**: Easy
```python
# Read a CSV file and perform calculations
# Output formatted results
```

---

## Week 7 - SQL
### Exercise 7.1: 50 SQL Queries
**Difficulty**: Medium
```sql
-- Practice 50 common SQL queries
-- Using movies.db and songs.db databases
```

### Exercise 7.2: Database Design
**Difficulty**: Medium
```sql
-- Design a database for a library system
-- Create tables with proper relationships
-- Write queries for common operations
```

### Exercise 7.3: SQL Injection Prevention
**Difficulty**: Easy
```python
# Identify and fix SQL injection vulnerabilities
# Convert string concatenation to parameterized queries
```

### Exercise 7.4: Aggregation Practice
**Difficulty**: Easy
```sql
-- Practice GROUP BY, HAVING, aggregate functions
-- Find top artists, average ratings, etc.
```

---

## Week 8 - HTML, CSS, JavaScript
### Exercise 8.1: Personal Homepage
**Difficulty**: Easy
```html
<!-- Build a personal homepage with:
- Header with name
- About section
- Projects list
- Contact form
- Responsive design -->
```

### Exercise 8.2: Interactive Trivia
**Difficulty**: Medium
```javascript
// Build a trivia quiz with:
- Multiple choice questions
- Score tracking
- Immediate feedback
- Final score display
```

### Exercise 8.3: CSS Grid Layout
**Difficulty**: Medium
```css
/* Create a responsive grid layout */
- Header spanning full width
- Sidebar and main content
- Footer
- Mobile-friendly
```

### Exercise 8.4: Form Validation
**Difficulty**: Medium
```javascript
// Validate a registration form:
- Required fields
- Email format
- Password strength
- Display error messages
```

---

## Week 9 - Flask
### Exercise 9.1: Finance Application
**Difficulty**: Hard
```python
# Build a stock trading simulation:
- User registration/login
- Buy/sell stocks
- Portfolio tracking
- Transaction history
```

### Exercise 9.2: URL Shortener
**Difficulty**: Medium
```python
# Build a URL shortener:
- Shorten URLs
- Redirect to original
- Track click counts
```

### Exercise 9.3: REST API
**Difficulty**: Medium
```python
# Build a REST API:
- GET /items - list all
- GET /items/:id - get one
- POST /items - create
- PUT /items/:id - update
- DELETE /items/:id - delete
```

### Exercise 9.4: Session Management
**Difficulty**: Easy
```python
# Implement:
- Login/logout
- Session tracking
- Protected routes
- Remember me functionality
```

---

## Final Project Ideas
1. **Web Application**: Blog, portfolio, or task manager
2. **Game**: Tic-tac-toe, connect four, or quiz game
3. **Data Tool**: Budget tracker, recipe manager, or inventory system
4. **API Client**: Weather app, news aggregator, or movie database
5. **Automation**: Email sender, file organizer, or report generator

## Difficulty Rating Guide
- **Easy**: 30-60 minutes, basic concepts
- **Medium**: 1-2 hours, multiple concepts combined
- **Hard**: 2-4 hours, complex logic and multiple files

## Tips for Solving
1. Read the problem completely before coding
2. Write pseudocode first
3. Start with the simplest test case
4. Test incrementally
5. Debug with printf/print statements
6. Check memory usage with Valgrind (C)
