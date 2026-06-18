# CS 4320/5320 — Syllabus Breakdown

## Course Structure

Based on [Cornell CS 4320 Fall 2021](https://www.cs.cornell.edu/courses/cs4320/2021fa/). Lectures at [www.databaselecture.com](http://www.databaselecture.com).

---

## Module 1: Introduction & Relational Model (Weeks 1–3)

### Lecture 1–2: Course Intro, Why Databases?
- Database vs. file system
- DBMS architecture (in-memory vs. on-disk, buffer management)
- Data models: relational, document, graph, key-value

### Lecture 3–4: Relational Model Fundamentals
- Relations, tuples, attributes, domains
- Relational algebra: select (σ), project (π), join (⋈), union, set difference
- Relational calculus: tuple and domain variants
- Keys: primary, foreign, candidate, composite

### Lecture 5–6: SQL Basics
- DDL: CREATE TABLE, ALTER, DROP
- DML: SELECT, INSERT, UPDATE, DELETE
- Filtering: WHERE, LIKE, BETWEEN, IN, IS NULL
- JOIN types: INNER, LEFT/RIGHT/FULL OUTER, CROSS, NATURAL

---

## Module 2: SQL Deep Dive (Weeks 4–6)

### Lecture 7–8: Advanced SQL
- Aggregation: GROUP BY, HAVING, aggregate functions (COUNT, SUM, AVG, MIN, MAX)
- Subqueries: correlated vs. uncorrelated, EXISTS, IN, ANY/ALL
- Set operations: UNION, INTERSECT, EXCEPT

### Lecture 9–10: SQL Expressions & Constraints
- Window functions: ROW_NUMBER, RANK, DENSE_RANK, LAG/LEAD
- CASE expressions, COALESCE, NULLIF
- Integrity constraints: PRIMARY KEY, FOREIGN KEY, UNIQUE, NOT NULL, CHECK
- Assertions and triggers

### Lecture 11–12: Views & Authorization
- Virtual views, materialized views
- CREATE VIEW, WITH CHECK OPTION
- GRANT/REVOKE permissions
- Role-based access control

---

## Module 3: Schema Design & Normalization (Weeks 7–9)

### Lecture 13–14: ER Modeling
- Entity types, attributes, relationships
- Cardinality constraints (1:1, 1:N, M:N)
- Participation constraints (total vs. partial)
- ISA hierarchies, aggregation, composition

### Lecture 15–16: Relational Schema Mapping
- ER to relational mapping rules
- Handling ISA hierarchies: single table, separate tables, shared table
- Mapping weak entities and multi-valued attributes

### Lecture 17–18: Normalization
- Functional dependencies (FDs)
- 1NF, 2NF, 3NF, BCNF
- Decomposition algorithms
- Lossless-join decomposition
- Dependency preservation
- Minimal cover

---

## Module 4: Query Processing & Optimization (Weeks 10–12)

### Lecture 19–20: Relational Algebra Equivalence
- Equivalence rules for relational algebra
- Join selection pushdown
- Projection pushdown
- Reducing the size of intermediate results

### Lecture 21–22: Cost-Based Query Optimization
- System catalog / statistics
- Selectivity estimation
- Access path costs: sequential scan, index scan, index-only
- Join algorithms: nested loop, sort-merge, hash join
- Join ordering (dynamic programming approach)

### Lecture 23–24: Indexing
- File organization: heap, sorted, clustered
- B+ tree: structure, search, insert, delete
- Hash indexes: static, extendible, linear hashing
- Composite indexes, covering indexes
- Index selection and tuning

---

## Module 5: Transactions & Concurrency Control (Weeks 13–14)

### Lecture 25–26: Transaction Concepts
- ACID: Atomicity, Consistency, Isolation, Durability
- Transaction states: active, partially committed, failed, aborted
- Schedule: serial, serializable, view serializable, conflict serializable
- Conflict equivalence and precedence graphs

### Lecture 27–28: Concurrency Control
- Two-Phase Locking (2PL): basic, conservative, strict
- Lock types: S (shared), X (exclusive), intention locks
- Deadlock: detection (wait-for graph), prevention (wait-die, wound-wait)
- Timestamp-based concurrency control
- Multi-Version Concurrency Control (MVCC)

### Lecture 29: Recovery
- ARIES recovery algorithm
- Write-ahead logging (WAL)
- Checkpointing
- Buffer management and steal/no-steal policies

---

## Module 6: Modern Data Systems (Weeks 15–16)

### Lecture 30–31: NoSQL
- CAP theorem (Brewer's conjecture)
- PACELC framework
- Key-value stores: Redis, DynamoDB
- Document stores: MongoDB, CouchDB
- Column-family: Cassandra, HBase
- Graph databases: Neo4j, Amazon Neptune

### Lecture 32: NewSQL & Distributed Databases
- Spanner, CockroachDB, YugabyteDB
- Consensus protocols: Raft, Paxos
- Distributed transactions: 2PC, 3PC
- Consistency levels: strong, eventual, causal

### Lecture 33: Stream & Spatial Data
- Stream processing: Kafka, Flink, Spark Streaming
- Windowed aggregation, event time vs. processing time
- Spatial data types: points, polygons, bounding boxes
- R-tree indexes, spatial queries
- PostGIS, MongoDB geospatial

---

## Assessment Structure (typical)

| Component | Weight |
|-----------|--------|
| Assignments (4–5) | 40% |
| Midterm | 20% |
| Final | 30% |
| Participation / Quizzes | 10% |

## Prerequisites

- CS 2110 (OOP & Data Structures) or equivalent
- Basic familiarity with algorithms and discrete math
