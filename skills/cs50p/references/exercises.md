# CS50P Practice Problems

## Week 0: Functions, Variables

### Problem 1: Hello, World
Write a program that prints "Hello, World" to the screen.

```python
# Your code here
print("Hello, World")
```

### Problem 2: Tip Calculator
Create a program that calculates the tip amount and total bill.

```python
# Input: bill amount and tip percentage
bill = float(input("Bill amount: "))
tip_percent = float(input("Tip percentage: "))

# Calculate and display
tip = bill * (tip_percent / 100)
total = bill + tip
print(f"Tip: ${tip:.2f}")
print(f"Total: ${total:.2f}")
```

### Problem 3: Calculator
Build a simple calculator that performs basic operations.

```python
num1 = float(input("First number: "))
op = input("Operator (+, -, *, /): ")
num2 = float(input("Second number: "))

if op == "+":
    result = num1 + num2
elif op == "-":
    result = num1 - num2
elif op == "*":
    result = num1 * num2
elif op == "/":
    result = num1 / num2
else:
    result = "Invalid operator"

print(f"Result: {result}")
```

---

## Week 1: Conditionals

### Problem 1: Grade Calculator
Convert a numerical grade to a letter grade.

```python
score = int(input("Enter score (0-100): "))

if score >= 90:
    grade = "A"
elif score >= 80:
    grade = "B"
elif score >= 70:
    grade = "C"
elif score >= 60:
    grade = "D"
else:
    grade = "F"

print(f"Grade: {grade}")
```

### Problem 2: Rock, Paper, Scissors
Create a Rock, Paper, Scissors game against the computer.

```python
import random

choices = ["rock", "paper", "scissors"]
computer = random.choice(choices)
player = input("Choose rock, paper, or scissors: ").lower()

if player == computer:
    print("It's a tie!")
elif (player == "rock" and computer == "scissors") or \
     (player == "paper" and computer == "rock") or \
     (player == "scissors" and computer == "paper"):
    print("You win!")
else:
    print("Computer wins!")
```

### Problem 3: Eligibility Checker
Check if a user is eligible to vote.

```python
age = int(input("Enter your age: "))
citizen = input("Are you a citizen? (yes/no): ").lower() == "yes"

if age >= 18 and citizen:
    print("You are eligible to vote!")
else:
    print("You are not eligible to vote.")
```

---

## Week 2: Loops

### Problem 1: Number Guessing Game
Create a number guessing game where the user tries to guess a secret number.

```python
import random

secret = random.randint(1, 100)
attempts = 0

while True:
    guess = int(input("Guess a number (1-100): "))
    attempts += 1
    
    if guess == secret:
        print(f"Congratulations! You guessed it in {attempts} attempts!")
        break
    elif guess < secret:
        print("Too low!")
    else:
        print("Too high!")
```

### Problem 2: Print Patterns
Print various patterns using loops.

```python
# Triangle pattern
n = 5
for i in range(1, n + 1):
    print("*" * i)

# Diamond pattern
n = 5
for i in range(1, n + 1):
    print(" " * (n - i) + "*" * (2 * i - 1))
for i in range(n - 1, 0, -1):
    print(" " * (n - i) + "*" * (2 * i - 1))
```

### Problem 3: Find Factors
Find all factors of a given number.

```python
num = int(input("Enter a number: "))

print(f"Factors of {num}:")
for i in range(1, num + 1):
    if num % i == 0:
        print(i, end=" ")
print()
```

---

## Week 3: Exceptions

### Problem 1: Input Validation
Validate user input with proper error handling.

```python
while True:
    try:
        age = int(input("Enter your age: "))
        if age < 0:
            raise ValueError("Age cannot be negative")
        break
    except ValueError as e:
        print(f"Invalid input: {e}. Please try again.")

print(f"Your age is {age}")
```

### Problem 2: Safe Division
Create a division calculator that handles errors.

```python
try:
    num1 = float(input("Numerator: "))
    num2 = float(input("Denominator: "))
    result = num1 / num2
except ZeroDivisionError:
    print("Error: Cannot divide by zero")
except ValueError:
    print("Error: Please enter valid numbers")
else:
    print(f"Result: {result}")
finally:
    print("Calculation complete")
```

### Problem 3: File Reading
Read a file with proper error handling.

```python
filename = input("Enter filename: ")

try:
    with open(filename, "r") as file:
        content = file.read()
        print(f"File contents:\n{content}")
except FileNotFoundError:
    print(f"Error: File '{filename}' not found")
except PermissionError:
    print(f"Error: Permission denied to read '{filename}")
except Exception as e:
    print(f"Error: {e}")
```

---

## Week 4: Libraries

### Problem 1: Random Password Generator
Generate a random password with specified length.

```python
import random
import string

length = int(input("Password length: "))
characters = string.ascii_letters + string.digits + string.punctuation
password = "".join(random.choices(characters, k=length))
print(f"Generated password: {password}")
```

### Problem 2: Statistics Calculator
Calculate mean, median, and mode of a list.

```python
import statistics

numbers = [1, 2, 3, 4, 5, 5, 6, 7, 8, 9, 10]

mean = statistics.mean(numbers)
median = statistics.median(numbers)
mode = statistics.mode(numbers)

print(f"Mean: {mean}")
print(f"Median: {median}")
print(f"Mode: {mode}")
```

### Problem 3: Coin Flip Simulator
Simulate flipping a coin multiple times.

```python
import random

flips = int(input("Number of flips: "))
heads = 0
tails = 0

for _ in range(flips):
    if random.choice(["heads", "tails"]) == "heads":
        heads += 1
    else:
        tails += 1

print(f"Heads: {heads} ({heads/flips*100:.1f}%)")
print(f"Tails: {tails} ({tails/flips*100:.1f}%)")
```

---

## Week 5: Unit Tests

### Problem 1: Test Calculator
Write tests for a calculator function.

```python
# calculator.py
def add(a, b):
    return a + b

def subtract(a, b):
    return a - b

def multiply(a, b):
    return a * b

def divide(a, b):
    if b == 0:
        raise ValueError("Cannot divide by zero")
    return a / b
```

```python
# test_calculator.py
import pytest
from calculator import add, subtract, multiply, divide

def test_add():
    assert add(2, 3) == 5
    assert add(-1, 1) == 0
    assert add(0.1, 0.2) == pytest.approx(0.3)

def test_subtract():
    assert subtract(5, 3) == 2
    assert subtract(0, 5) == -5

def test_multiply():
    assert multiply(3, 4) == 12
    assert multiply(-2, 3) == -6
    assert multiply(0, 100) == 0

def test_divide():
    assert divide(10, 2) == 5
    assert divide(1, 3) == pytest.approx(0.3333)
    
def test_divide_by_zero():
    with pytest.raises(ValueError):
        divide(1, 0)
```

### Problem 2: Test String Functions
Write tests for string manipulation functions.

```python
# string_utils.py
def capitalize_words(s):
    return " ".join(word.capitalize() for word in s.split())

def is_palindrome(s):
    cleaned = s.lower().replace(" ", "")
    return cleaned == cleaned[::-1]
```

```python
# test_string_utils.py
from string_utils import capitalize_words, is_palindrome

def test_capitalize_words():
    assert capitalize_words("hello world") == "Hello World"
    assert capitalize_words("python programming") == "Python Programming"

def test_is_palindrome():
    assert is_palindrome("racecar") == True
    assert is_palindrome("hello") == False
    assert is_palindrome("A man a plan a canal Panama") == True
```

---

## Week 6: File I/O

### Problem 1: Read and Process Text File
Read a file and count word frequencies.

```python
def count_words(filename):
    word_count = {}
    try:
        with open(filename, "r") as file:
            for line in file:
                words = line.lower().split()
                for word in words:
                    word = word.strip(".,!?;:\"'")
                    word_count[word] = word_count.get(word, 0) + 1
        return word_count
    except FileNotFoundError:
        print(f"File '{filename}' not found")
        return {}

# Usage
filename = input("Enter filename: ")
counts = count_words(filename)
for word, count in sorted(counts.items(), key=lambda x: x[1], reverse=True):
    print(f"{word}: {count}")
```

### Problem 2: Write CSV File
Create and write data to a CSV file.

```python
import csv

def create_student_report(students, filename):
    with open(filename, "w", newline="") as file:
        writer = csv.writer(file)
        writer.writerow(["Name", "Grade", "Score"])
        for student in students:
            writer.writerow([student["name"], student["grade"], student["score"]])

# Sample data
students = [
    {"name": "Alice", "grade": "A", "score": 95},
    {"name": "Bob", "grade": "B", "score": 85},
    {"name": "Charlie", "grade": "A", "score": 92}
]

create_student_report(students, "report.csv")
print("Report created successfully!")
```

### Problem 3: JSON Data Store
Create a simple JSON-based data storage system.

```python
import json

def load_data(filename="data.json"):
    try:
        with open(filename, "r") as file:
            return json.load(file)
    except FileNotFoundError:
        return {"contacts": []}

def save_data(data, filename="data.json"):
    with open(filename, "w") as file:
        json.dump(data, file, indent=2)

def add_contact(name, phone, email):
    data = load_data()
    data["contacts"].append({
        "name": name,
        "phone": phone,
        "email": email
    })
    save_data(data)

# Usage
add_contact("Alice", "555-1234", "alice@example.com")
print("Contact added!")
```

---

## Week 7: Regular Expressions

### Problem 1: Email Validation
Validate email addresses using regex.

```python
import re

def is_valid_email(email):
    pattern = r"^[\w\.-]+@[\w\.-]+\.\w+$"
    return bool(re.match(pattern, email))

# Test cases
emails = [
    "user@example.com",
    "invalid@",
    "test.email@domain.org",
    "@missing.com"
]

for email in emails:
    print(f"{email}: {'Valid' if is_valid_email(email) else 'Invalid'}")
```

### Problem 2: Extract Phone Numbers
Extract phone numbers from text.

```python
import re

def extract_phones(text):
    pattern = r"\b\d{3}[-.]?\d{3}[-.]?\d{4}\b"
    return re.findall(pattern, text)

# Sample text
text = "Call me at 555-123-4567 or 555.987.6543. My office is 5551112222."
phones = extract_phones(text)
print("Phone numbers found:", phones)
```

### Problem 3: Parse Log Files
Parse and analyze log files using regex.

```python
import re

def parse_log(filename):
    pattern = r"(\d{4}-\d{2}-\d{2} \d{2}:\d{2}:\d{2}) \[(\w+)\] (.+)"
    logs = []
    
    try:
        with open(filename, "r") as file:
            for line in file:
                match = re.match(pattern, line.strip())
                if match:
                    timestamp, level, message = match.groups()
                    logs.append({
                        "timestamp": timestamp,
                        "level": level,
                        "message": message
                    })
        return logs
    except FileNotFoundError:
        print(f"Log file '{filename}' not found")
        return []

# Usage
logs = parse_log("app.log")
for log in logs:
    print(f"[{log['timestamp']}] {log['level']}: {log['message']}")
```

---

## Week 8: Object-Oriented Programming

### Problem 1: BankAccount Class
Create a bank account class with deposit and withdrawal.

```python
class BankAccount:
    def __init__(self, owner, balance=0):
        self.owner = owner
        self.balance = balance
    
    def deposit(self, amount):
        if amount <= 0:
            raise ValueError("Deposit amount must be positive")
        self.balance += amount
        return f"Deposited ${amount}. New balance: ${self.balance}"
    
    def withdraw(self, amount):
        if amount <= 0:
            raise ValueError("Withdrawal amount must be positive")
        if amount > self.balance:
            raise ValueError("Insufficient funds")
        self.balance -= amount
        return f"Withdrew ${amount}. New balance: ${self.balance}"
    
    def __str__(self):
        return f"BankAccount({self.owner}, ${self.balance})"

# Usage
account = BankAccount("Alice", 1000)
print(account.deposit(500))
print(account.withdraw(200))
print(account)
```

### Problem 2: Deck of Cards
Create a deck of cards class.

```python
import random

class Card:
    def __init__(self, suit, rank):
        self.suit = suit
        self.rank = rank
    
    def __repr__(self):
        return f"{self.rank} of {self.suit}"

class Deck:
    def __init__(self):
        suits = ["Hearts", "Diamonds", "Clubs", "Spades"]
        ranks = ["2", "3", "4", "5", "6", "7", "8", "9", "10",
                 "Jack", "Queen", "King", "Ace"]
        self.cards = [Card(suit, rank) for suit in suits for rank in ranks]
        self.shuffle()
    
    def shuffle(self):
        random.shuffle(self.cards)
    
    def deal(self, num_cards=1):
        if num_cards > len(self.cards):
            raise ValueError("Not enough cards in deck")
        return [self.cards.pop() for _ in range(num_cards)]

# Usage
deck = Deck()
hand = deck.deal(5)
print("Your hand:", hand)
```

### Problem 3: Student Grade System
Create a student grade management system.

```python
class Student:
    def __init__(self, name):
        self.name = name
        self.grades = []
    
    def add_grade(self, grade):
        if grade < 0 or grade > 100:
            raise ValueError("Grade must be between 0 and 100")
        self.grades.append(grade)
    
    def average(self):
        if not self.grades:
            return 0
        return sum(self.grades) / len(self.grades)
    
    def letter_grade(self):
        avg = self.average()
        if avg >= 90:
            return "A"
        elif avg >= 80:
            return "B"
        elif avg >= 70:
            return "C"
        elif avg >= 60:
            return "D"
        else:
            return "F"
    
    def __str__(self):
        return f"{self.name}: {self.average():.1f}% ({self.letter_grade()})"

# Usage
student = Student("Alice")
student.add_grade(95)
student.add_grade(87)
student.add_grade(92)
print(student)
```

---

## Week 9: Advanced Topics

### Problem 1: Caching Decorator
Create a decorator that caches function results.

```python
def cache(func):
    cache_dict = {}
    def wrapper(*args):
        if args in cache_dict:
            print(f"Cache hit for {args}")
            return cache_dict[args]
        result = func(*args)
        cache_dict[args] = result
        return result
    return wrapper

@cache
def fibonacci(n):
    if n < 2:
        return n
    return fibonacci(n-1) + fibonacci(n-2)

# Test
print(fibonacci(10))  # Should use cache
print(fibonacci(20))  # Should use cache
```

### Problem 2: Number Generator
Create a generator that yields numbers in a range.

```python
def number_generator(start, end, step=1):
    current = start
    while current <= end:
        yield current
        current += step

# Usage
for num in number_generator(1, 10, 2):
    print(num, end=" ")  # 1 3 5 7 9
print()

# List comprehension with generator
squares = [x**2 for x in number_generator(1, 10)]
print(squares)
```

### Problem 3: Data Transformation
Transform data using comprehensions and lambdas.

```python
# Sample data
students = [
    {"name": "Alice", "score": 95},
    {"name": "Bob", "score": 85},
    {"name": "Charlie", "score": 92},
    {"name": "Diana", "score": 78}
]

# List comprehension - filter and transform
honor_roll = [s["name"] for s in students if s["score"] >= 90]
print(f"Honor Roll: {honor_roll}")

# Dictionary comprehension - create lookup
score_lookup = {s["name"]: s["score"] for s in students}
print(f"Score lookup: {score_lookup}")

# Lambda with map
names = list(map(lambda s: s["name"].upper(), students))
print(f"Uppercase names: {names}")

# Lambda with filter
high_scorers = list(filter(lambda s: s["score"] >= 90, students))
print(f"High scorers: {[s['name'] for s in high_scorers]}")
```

## Tips for Practice

1. **Start simple** - Begin with basic versions, then add complexity
2. **Test as you go** - Write small tests to verify your code
3. **Read error messages** - Python's error messages are helpful
4. **Use the debugger** - VS Code's debugger is powerful for learning
5. **Comment your code** - Explain what you're doing and why
6. **Refactor** - Improve your code after getting it working
7. **Challenge yourself** - Try to solve problems multiple ways