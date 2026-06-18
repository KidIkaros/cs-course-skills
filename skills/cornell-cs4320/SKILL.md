---
name: "cornell-cs4320"
description: "Cornell CS 4320 - Introduction to Database Systems. Use when learning SQL, relational databases, query optimization, transactions, ACID, NoSQL, or designing database schemas. Covers both theory and practical systems."
compatibility: opencode
metadata:
  university: "Cornell University"
  level: "intermediate-advanced"
  topics: ["SQL", "databases", "query optimization", "transactions", "NoSQL", "schema design"]
  url: "https://www.cs.cornell.edu/courses/cs4320/2021fa/"
---

# Cornell CS 4320 — Introduction to Database Systems

## Overview

This skill covers the core material from Cornell's CS 4320/5320, a rigorous course on relational databases, query processing, and modern data systems. Use this when working with SQL, designing schemas, tuning queries, understanding transaction guarantees, or evaluating NoSQL/NewSQL tradeoffs.

## When to Use

- Writing or optimizing SQL queries
- Designing relational schemas (normalization, ER modeling)
- Debugging transaction isolation issues
- Explaining ACID properties
- Choosing between SQL and NoSQL for a use case
- Understanding query plans and indexing strategies
- Working with graph, stream, or spatial data systems

## Core Topics

### 1. Relational Model & SQL
- Relational algebra and calculus
- SQL: DDL, DML, nested queries, aggregation, window functions
- Views, integrity constraints, triggers

### 2. Schema Design
- ER diagrams, EER modeling
- Normalization (1NF through BCNF)
- Decomposition and lossless-join / dependency preservation

### 3. Query Processing & Optimization
- Relational algebra equivalence rules
- Cost-based optimization, join ordering
- Index-based access paths, hash vs. B+ tree indexes
- Query plan interpretation and EXPLAIN analysis

### 4. Transactions & Concurrency
- ACID properties and their guarantees
- Schedule equivalence, serializability
- Two-phase locking (2PL), MVCC
- Deadlock detection and prevention
- Isolation levels: Read Uncommitted through Serializable

### 5. Modern Data Systems
- NoSQL: key-value, document, column-family, graph stores
- NewSQL: Spanner, CockroachDB, YugabyteDB
- Distributed transactions, CAP theorem, PACELC
- Stream processing and spatial databases

## Key References

- **Textbook**: *Database Management Systems* (Ramakrishnan & Gehrke)
- **Lectures**: [www.databaselecture.com](http://www.databaselecture.com)
- **Course page**: [cs4320 2021fa](https://www.cs.cornell.edu/courses/cs4320/2021fa/)

## File Index

| File | Purpose |
|------|---------|
| `references/syllabus.md` | Week-by-week topic breakdown |
| `references/key-concepts.md` | Cheat sheet for SQL, transactions, indexing |
| `references/exercises.md` | Practice SQL, schema design, optimization problems |
| `references/resources.md` | Textbooks, papers, tools, lectures |

## See Also

- `cs50-web` - Harvard CS50 Web - Web Programming with Python and JavaScript
- `cornell-cs6120` - Cornell CS 6120 - Advanced Compilers
