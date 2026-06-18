# CS 4320 — Practice Exercises

Work through these to build proficiency in SQL, schema design, and query optimization.

---

## Section 1: SQL Queries

### Schema
```sql
CREATE TABLE Students (
    sid INT PRIMARY KEY,
    name VARCHAR(100),
    age INT,
    gpa DECIMAL(3,2)
);

CREATE TABLE Courses (
    cid VARCHAR(10) PRIMARY KEY,
    title VARCHAR(200),
    dept VARCHAR(50),
    credits INT
);

CREATE TABLE Enrollments (
    sid INT,
    cid VARCHAR(10),
    semester VARCHAR(10),
    grade VARCHAR(2),
    PRIMARY KEY (sid, cid, semester),
    FOREIGN KEY (sid) REFERENCES Students(sid),
    FOREIGN KEY (cid) REFERENCES Courses(cid)
);

CREATE TABLE Professors (
    pid INT PRIMARY KEY,
    name VARCHAR(100),
    dept VARCHAR(50),
    salary DECIMAL(10,2)
);

CREATE TABLE Teaching (
    pid INT,
    cid VARCHAR(10),
    semester VARCHAR(10),
    PRIMARY KEY (pid, cid, semester)
);
```

### Basic Queries

**Q1**: Find all students with GPA above 3.5, ordered by GPA descending.

**Q2**: Find the number of students enrolled in each course for Fall 2021.

**Q3**: Find courses that have more than 50 students in any semester.

**Q4**: Find students who have never enrolled in any course.

**Q5**: Find the average GPA of students in each course (for students who took that course).

### Intermediate Queries

**Q6**: Find the top 3 students (by GPA) who have taken at least 3 courses.

**Q7**: For each department, find the course with the highest average grade. (Assume grades are numeric: A=4, B=3, C=2, D=1, F=0.)

**Q8**: Find pairs of students who have taken the exact same set of courses.

**Q9**: Find professors who have taught at least one course in every semester offered.

**Q10**: Find students whose GPA is above the average GPA of students in their age group (age groups: 18–20, 21–23, 24+).

### Advanced Queries

**Q11**: Find the longest consecutive sequence of semesters where a student was enrolled in at least one course.

**Q12**: For each student, find the grade difference between their best and worst course.

**Q13**: Rank students within each department based on total credits completed (assume 3 credits per course unless specified).

**Q14**: Find students who have taken courses from every professor in the CS department.

**Q15**: Produce a " transcript" showing each student, each course taken, the grade, and a running GPA.

---

## Section 2: Schema Design

### Problem A: University Library
Design a schema for a university library system:
- Books (ISBN, title, author(s), publisher, year)
- Members (ID, name, department, type: UG/Grad/Faculty)
- Loans (book, member, checkout date, due date, return date)
- Reservations (book, member, date, status)
- Requirements:
  - A book can have multiple authors
  - Members can reserve only if all copies are checked out
  - Faculty can check out up to 20 books, students up to 5

### Problem B: E-Commerce Platform
Design a schema for an e-commerce platform:
- Products (ID, name, description, price, category)
- Categories (hierarchical: Electronics > Phones > Smartphones)
- Users (ID, name, email, address(es))
- Orders (ID, user, items, quantities, total, status, date)
- Reviews (user, product, rating, text, date)
- Inventory (product, warehouse, stock)
- Requirements:
  - A product can be in multiple categories
  - Support product variants (size, color) with separate inventory
  - Price can change but order history should reflect original price

### Problem C: Social Network
Design a schema for a social network:
- Users (ID, name, email, join date)
- Posts (ID, author, content, timestamp, visibility)
- Comments (ID, post, author, content, timestamp)
- Likes (user, post, timestamp)
- Follows (follower, followee, date)
- Groups (ID, name, description, privacy)
- Group membership (user, group, role, join date)
- Requirements:
  - Support threaded comments (replies to comments)
  - A post can be public, friends-only, or private
  - Group admins can remove members

---

## Section 3: Normalization

### Problem D: Given the relation and FDs, decompose to BCNF

**Relation**: R(A, B, C, D, E)

**FDs**:
- A → B, C
- B → D
- C → E
- A, D → C

**Tasks**:
1. Find the candidate key(s)
2. Check if R is in 3NF. If not, decompose.
3. Check if the decomposition is in BCNF.
4. Verify lossless join property.
5. Check dependency preservation.

### Problem E: Normalize this design

**Unnormalized table**:
```
StudentCourses(sid, name, gpa, courses)
```
Where `courses` is a comma-separated list of (cid, title, grade).

1. Convert to 1NF
2. Convert to 2NF
3. Convert to 3NF
4. Convert to BCNF
5. Show the schema at each step

---

## Section 4: Query Optimization

### Problem F: Optimize these queries

**Q1**: Given this query and the schema from Section 1:
```sql
SELECT s.name
FROM Students s, Enrollments e, Courses c
WHERE s.sid = e.sid
  AND e.cid = c.cid
  AND c.dept = 'CS'
  AND s.gpa > 3.5;
```
a) Write the relational algebra tree
b) Apply optimization rules to produce a better plan
c) Estimate relative costs (assume 10K students, 50K enrollments, 500 courses, 10% CS courses)

**Q2**: Given this correlated subquery:
```sql
SELECT s.name
FROM Students s
WHERE s.gpa > (
    SELECT AVG(gpa)
    FROM Students
    WHERE dept = s.dept
);
```
a) Rewrite as a JOIN
b) Compare the cost of the subquery version vs. the JOIN version
c) Under what data distribution would the JOIN be slower?

### Problem G: Index Design

For the Student/Course/Enrollment schema, design indexes for these query workloads:

**Workload 1**: Find students by GPA range
**Workload 2**: Find all courses taken by a specific student
**Workload 3**: Find the top student in each course
**Workload 4**: Find all enrollments for a given semester + department
**Workload 5**: Update student GPA by ID

For each, specify:
- Which index(es) to create
- Column(s) and order
- B+ tree vs. hash
- Brief justification

---

## Section 5: Transactions

### Problem H: Serializability

Given these transactions:
- T1: R(A), W(A), R(B), W(B)
- T2: R(B), W(B), R(C), W(C)
- T3: R(A), W(A), R(C), W(C)

For each schedule, determine if it's:
1. Conflict serializable
2. View serializable
3. If serializable, give an equivalent serial order

**Schedule 1**: R1(A), R2(B), W1(A), W2(B), R3(A), R3(C), W1(B), W2(C), W3(A), W3(C)

**Schedule 2**: R1(A), R3(C), R2(B), W1(A), W3(C), W2(B), R1(B), W2(C), W3(A), W1(B)

### Problem I: Locking

Given a database with items A, B, C, D and transactions:
- T1: R(A), W(A), R(B), W(B)
- T2: R(B), W(B), R(C), W(C)
- T3: R(A), R(C)

Show the lock sequences for:
1. Basic 2PL
2. Strict 2PL
3. Identify any deadlock situations
4. Show how wait-die or wound-wait prevents deadlock

---

## Solutions Approach

For SQL problems, test your solutions using PostgreSQL, MySQL, or SQLite. For schema design problems, draw ER diagrams first, then map to relational schemas. For optimization problems, use EXPLAIN ANALYZE to verify cost estimates.
