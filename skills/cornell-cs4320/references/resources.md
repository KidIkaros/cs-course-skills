# CS 4320 — Resources

## Course Materials

| Resource | URL |
|----------|-----|
| Course Page (Fall 2021) | https://www.cs.cornell.edu/courses/cs4320/2021fa/ |
| Video Lectures | http://www.databaselecture.com |
| CS 4320 Archive (Spring 2020) | https://www.cs.cornell.edu/courses/cs4320/2020sp/ |

---

## Textbook

**Database Management Systems** (3rd Edition)
- Authors: Ramakrishnan & Gehrke
- Also known as "the cow book" (cover has a cow)
- Not freely available, but widely used in university courses
- Solutions to some exercises circulate online

**Alternative / Supplementary**:
- *Database System Concepts* (7th Ed.) — Silberschatz, Korth, Sudarshan
- *Readings in Database Systems* (The Red Book) — Bailis, Hellerstein, Stonebraker (free online: http://www.redbook.io)

---

## Lectures (databaselecture.com)

Full video lecture series covering the entire course. Topics match Cornell CS 4320.

| Module | Topics |
|--------|--------|
| Relational Model | Relations, algebra, calculus, keys |
| SQL | DDL, DML, joins, aggregation, subqueries |
| Schema Design | ER modeling, normalization, BCNF |
| Query Processing | Cost models, join algorithms, optimization |
| Indexing | B+ trees, hash indexes, index selection |
| Transactions | ACID, serializability, 2PL, MVCC |
| Modern Systems | NoSQL, NewSQL, CAP theorem |

---

## Papers (Foundational)

| Paper | Authors | Year | Topic |
|-------|---------|------|-------|
| A Relational Model of Data for Large Shared Data Banks | Codd | 1970 | Original relational model |
| The Original ACID Paper | Haerder & Reuter | 1983 | ACID properties formalized |
| Harvest, Yield, and Scalable Tolerant Systems | Fox & Brewer | 1999 | CAP theorem origin |
| Dynamo: Amazon's Highly Available Key-Value Store | DeCandia et al. | 2007 | Dynamo-style NoSQL |
| Spanner: Google's Globally-Distributed Database | Corbett et al. | 2012 | NewSQL pioneer |
| F1: A Distributed SQL Database That Scales | Shute et al. | 2013 | Spanner application layer |
| The Log-Structured Merge-Tree | O'Neil et al. | 1996 | LSM-tree (used in Cassandra, RocksDB) |
| Write-Ahead Logging (ARIES) | Mohan et al. | 1992 | Recovery algorithm |

---

## Tools

### Practice Databases

| Tool | Type | Use Case |
|------|------|----------|
| PostgreSQL | RDBMS | Full-featured SQL practice |
| SQLite | Embedded | Lightweight, file-based |
| MySQL | RDBMS | Web-oriented, widespread |
| DuckDB | Analytical | Columnar, fast OLAP |

### Query Visualization

| Tool | URL | Purpose |
|------|-----|---------|
| EXPLAIN (PostgreSQL) | built-in | Query plan analysis |
| pgAdmin | https://www.pgadmin.org | GUI for PostgreSQL |
| DBeaver | https://dbeaver.io | Universal DB client |
| DB Fiddle | https://www.db-fiddle.com | Online SQL sandbox |

### Schema Design

| Tool | URL | Purpose |
|------|-----|---------|
| dbdiagram.io | https://dbdiagram.io | ER diagrams (DBML) |
| SchemaSpy | http://schemaspy.org | Schema visualization |
| QuickDBD | https://quickdatabasediagrams.com | Quick ER sketches |

### NoSQL / NewSQL Practice

| System | Type | Getting Started |
|--------|------|-----------------|
| MongoDB | Document | Free tier on MongoDB Atlas |
| Redis | Key-value | `docker run redis` |
| Cassandra | Column-family | AstraDB free tier |
| Neo4j | Graph | Free desktop + AuraDB |
| CockroachDB | NewSQL | Free tier, Postgres-compatible |
| TiDB | NewSQL | Free tier, Postgres-compatible |

---

## Online Practice

| Resource | URL | What |
|----------|-----|------|
| LeetCode Database | https://leetcode.com/problemset/database/ | SQL interview problems |
| HackerRank SQL | https://www.hackerrank.com/domains/sql | SQL practice by difficulty |
| SQLZoo | https://sqlzoo.net | Interactive SQL tutorials |
| Mode Analytics SQL Tutorial | https://mode.com/sql-tutorial/ | Practical SQL with examples |
| PostgreSQL Exercises | https://pgexercises.com | Schema design + queries |
| Use The Index, Luke | https://use-the-index-luke.com | Indexing deep dive |

---

## Related Cornell Courses

| Course | Title | Connection |
|--------|-------|------------|
| CS 4320/5320 | Intro to Database Systems | This course |
| CS 5320 | Advanced Database Systems | Deeper dive into research topics |
| CS 4300 | Language & Information | NLP, connects to text databases |
| CS 5850 | Network Science | Graph databases, network data |
| INFO 4300 | Digital Humanities | Applied database for humanities data |

---

## Cheat Sheets & References

- [SQL Cheat Sheet (SQLBolt)](https://sqlbolt.com/)
- [PostgreSQL Documentation](https://www.postgresql.org/docs/)
- [Use The Index, Luke](https://use-the-index-luke.com/) — free book on indexing
- [The Red Book](http://www.redbook.io/) — Readings in Database Systems (free)
