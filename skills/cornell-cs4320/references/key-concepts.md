# Database Concepts Cheat Sheet

Quick reference for the core concepts covered in CS 4320.

---

## SQL Essentials

### DDL (Schema Definition)
```sql
CREATE TABLE Students (
    sid    INT PRIMARY KEY,
    name   VARCHAR(100) NOT NULL,
    gpa    DECIMAL(3,2),
    dept   VARCHAR(50)
);

ALTER TABLE Students ADD email VARCHAR(255);
DROP TABLE Students;
```

### DML (Queries)
```sql
-- Basic select with filter
SELECT name, gpa FROM Students WHERE gpa > 3.5 ORDER BY gpa DESC;

-- Aggregation
SELECT dept, AVG(gpa) AS avg_gpa
FROM Students
GROUP BY dept
HAVING AVG(gpa) > 3.0;

-- Join
SELECT s.name, c.title
FROM Students s
JOIN Enrollments e ON s.sid = e.sid
JOIN Courses c ON e.cid = c.cid;

-- Window function
SELECT name, gpa,
       RANK() OVER (PARTITION BY dept ORDER BY gpa DESC) AS dept_rank
FROM Students;

-- Correlated subquery
SELECT name FROM Students s
WHERE gpa > (SELECT AVG(gpa) FROM Students WHERE dept = s.dept);

-- EXISTS
SELECT name FROM Students s
WHERE EXISTS (
    SELECT 1 FROM Enrollments e
    JOIN Courses c ON e.cid = c.cid
    WHERE e.sid = s.sid AND c.dept = 'CS'
);

-- CTE
WITH HighGPA AS (
    SELECT * FROM Students WHERE gpa >= 3.8
)
SELECT dept, COUNT(*) FROM HighGPA GROUP BY dept;
```

### Useful SQL Patterns
```sql
-- Find duplicate rows
SELECT col, COUNT(*) FROM table GROUP BY col HAVING COUNT(*) > 1;

-- Delete duplicates (keep min id)
DELETE FROM table WHERE id NOT IN (
    SELECT MIN(id) FROM table GROUP BY duplicate_cols
);

-- Running total
SELECT date, amount,
       SUM(amount) OVER (ORDER BY date) AS running_total
FROM transactions;

-- Gap-and-island (consecutive ranges)
SELECT MIN(start_date), MAX(end_date)
FROM (
    SELECT date,
           date - INTERVAL '1' * ROW_NUMBER() OVER (ORDER BY date) AS grp
    FROM dates
) sub
GROUP BY grp;
```

---

## Relational Algebra

| Operation | Symbol | Description |
|-----------|--------|-------------|
| Selection | σ(θ)(R) | Rows satisfying condition θ |
| Projection | π(A₁..An)(R) | Specific columns |
| Cartesian Product | R × S | All combinations |
| Natural Join | R ⋈ S | Join on shared attributes |
| Theta Join | R ⋈θ S | Join with condition |
| Left Outer Join | R ⟕ S | All of R + matched S |
| Union | R ∪ S | All rows from both |
| Set Difference | R − S | In R but not S |
| Intersection | R ∩ S | In both R and S |
| Rename | ρ(S)(R) | Rename relation/attributes |

---

## ACID Properties

| Property | Guarantee | Mechanism |
|----------|-----------|-----------|
| **Atomicity** | All or nothing | WAL, undo logging, 2PC |
| **Consistency** | Valid state transitions | Constraints, triggers, application logic |
| **Isolation** | Concurrent txns don't interfere | 2PL, MVCC, timestamps |
| **Durability** | Committed data persists | WAL, disk flush, replication |

---

## Transaction Isolation Levels

| Level | Dirty Read | Non-Repeatable Read | Phantom Read |
|-------|------------|---------------------|--------------|
| Read Uncommitted | Yes | Yes | Yes |
| Read Committed | No | Yes | Yes |
| Repeatable Read | No | No | Yes |
| Serializable | No | No | No |

---

## Concurrency Control

### Two-Phase Locking (2PL)
- **Growing phase**: acquire locks, no releases
- **Shrinking phase**: release locks, no acquires
- **Strict 2PL**: hold X-locks until commit/abort (prevents cascading aborts)

### Lock Types
- **Shared (S)**: allows reads, compatible with other S locks
- **Exclusive (X)**: allows reads + writes, no other locks compatible
- **Intention locks (IS, IX, SIX)**: hierarchical locking for tables with row locks

### Deadlock Handling
- **Detection**: build wait-for graph, find cycles
- **Prevention**: wait-die (older waits), wound-wait (younger waits)
- **Timeout**: abort transaction after N seconds

### MVCC
- Each write creates a new version
- Readers see a consistent snapshot
- No read-write blocking
- Garbage collection of old versions

---

## Indexing

### B+ Tree
- Balanced tree with high fanout
- All data at leaves (linked for range scans)
- Height: O(log n), typically 2–4 for millions of rows
- Good for: equality + range queries, ordering

### Hash Index
- O(1) lookup for equality queries
- No range scan support
- Extendible hashing: split buckets dynamically
- Good for: point lookups, joins on equality

### When to Use Which

| Query Pattern | Best Index |
|---------------|------------|
| `WHERE id = ?` | B+ tree or hash |
| `WHERE id BETWEEN ? AND ?` | B+ tree |
| `ORDER BY col` | B+ tree on col |
| `WHERE a = ? AND b = ?` | Composite B+ tree (a, b) |
| `SELECT col FROM t WHERE ...` | Covering index (includes col) |
| `GROUP BY col` | B+ tree on col |

---

## Normalization

### Functional Dependencies (FDs)
- X → Y means: knowing X determines Y
- Closure: X⁺ = set of all attributes determined by X
- Minimal cover: smallest equivalent set of FDs

### Normal Forms

| NF | Requirement |
|----|-------------|
| 1NF | Atomic values (no repeating groups) |
| 2NF | No partial dependencies on composite key |
| 3NF | No transitive dependencies |
| BCNF | For every FD X→Y, X is a superkey |

### Decomposition Properties
- **Lossless join**: reconstructing R from R₁ and R₂ yields no extra tuples
- **Dependency preservation**: all original FDs enforced by the decomposed tables

---

## Query Optimization Rules

1. Push selections down (reduce rows early)
2. Push projections down (reduce columns early)
3. Reorder joins (smallest intermediate result first)
4. Use indexes for selections and joins when possible
5. Avoid `SELECT *` — only retrieve needed columns
6. Replace `NOT IN (subquery)` with `NOT EXISTS` when possible
7. Use `EXISTS` instead of `IN` for correlated subqueries
8. Materialize CTEs when used multiple times (database-specific)

---

## CAP Theorem

You can guarantee **at most 2 of 3**:

- **Consistency**: every read receives the most recent write
- **Availability**: every request receives a response
- **Partition tolerance**: system continues despite network failures

In practice, networks always partition, so you choose between C and A.

### PACELC Extension
- **If Partition**: choose Availability or Consistency
- **Else (normal operation)**: choose Latency or Consistency
