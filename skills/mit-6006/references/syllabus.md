# MIT 6.006 — Syllabus Breakdown

## Unit 1: Introduction & Computational Complexity

### Lecture 1: Algorithms and Computation
- What is an algorithm?
- Specification: input → output
- Correctness: does it always produce the right answer?
- Efficiency: speed of execution
- RAM model of computation
- Counting operations

### Lecture 2: Computational Complexity: Models of Computation
- Random Access Machine (RAM) model
- Bit complexity
- Best/worst/average case analysis
- Big-O, Big-Theta, Big-Omega notation
- Growth of functions
- Common growth rates: O(1), O(log n), O(n), O(n log n), O(n²), O(2ⁿ), O(n!)

### Lecture 3: Sorting I
- Insertion sort: O(n²) worst case, O(n) best case
- Merge sort: O(n log n) worst case
- Divide and conquer paradigm
- Recurrences and the Master Theorem

## Unit 2: Sorting

### Lecture 4: Sorting II — Heapsort
- Heap data structure (binary heap)
- Array representation of heaps
- Heap operations: insert, extract-min/max — O(log n)
- Heapsort: O(n log n) worst case
- Priority queue applications

### Lecture 5: Sorting III — Lower Bounds & Linear-Time Sorting
- Decision tree model
- Ω(n log n) lower bound for comparison sorts
- Counting sort: O(n + k) — stable, non-comparison
- Radix sort: O(d(n + k)) — digit-by-digit

### Lecture 6: Sorting IV — Linear-Time Sorting
- Counting sort details and stability
- Radix sort: LSD vs MSD
- When to use each sorting algorithm
- Sorting in practice (Python's Timsort, introsort)

## Unit 3: Hashing

### Lecture 7: Hashing I
- Direct addressing (when universe is small)
- Hash functions: division method, multiplication method
- Collision resolution: chaining
- Simple uniform hashing assumption
- Expected O(1) operations with good hash functions

### Lecture 8: Hashing II
- Open addressing: linear probing, quadratic probing, double hashing
- Cluster formation and performance degradation
- Universal hash families
- Perfect hashing (static sets)
- Cuckoo hashing

## Unit 4: Graph Algorithms

### Lecture 9: Graphs I — Introduction & BFS
- Graph terminology: vertices, edges, directed/undirected, weighted/unweighted
- Adjacency list vs adjacency matrix representations
- Breadth-First Search (BFS)
- BFS properties: shortest paths in unweighted graphs
- BFS time complexity: O(V + E)
- BFS applications: connected components, bipartiteness testing

### Lecture 10: Graphs II — DFS
- Depth-First Search (DFS)
- DFS timestamps: discovery time, finish time
- Edge classification: tree, back, forward, cross
- DFS applications: cycle detection, topological sort
- Strongly connected components (Kosaraju's algorithm)
- DFS time complexity: O(V + E)

### Lecture 11: Graphs III — Dijkstra's Algorithm
- Single-source shortest paths (non-negative weights)
- Greedy approach with priority queue
- Dijkstra's algorithm: O((V + E) log V) with binary heap
- Dijkstra's correctness proof sketch
- Limitations: no negative weight edges

### Lecture 12: Graphs IV — Bellman-Ford & DAG Shortest Paths
- Bellman-Ford algorithm: O(VE)
- Negative weight cycle detection
- DAG shortest paths: O(V + E) using topological order
- Shortest paths in general weighted graphs
- Comparison of shortest path algorithms

## Unit 5: Dynamic Programming

### Lecture 13: Dynamic Programming I
- Optimal substructure property
- Overlapping subproblems
- Memoization (top-down) vs tabulation (bottom-up)
- Fibonacci numbers: O(n) with DP vs O(2ⁿ) naive recursion
- Rod cutting problem
- Matrix chain multiplication

### Lecture 14: Dynamic Programming II
- Parenthesization problem
- Edit distance (Levenshtein distance)
- LCS (Longest Common Subsequence)
- Knapsack problem (0/1 and unbounded)
- DP problem-solving recipe:
  1. Identify subproblems
  2. Define recurrence relation
  3. Choose memoization or tabulation
  4. Reconstruct solution

## Unit 6: Advanced Topics

### Lecture 15: NP-Completeness I
- Polynomial time (class P)
- Non-deterministic polynomial time (class NP)
- P vs NP question
- Polynomial-time reductions
- Decision problems and optimization problems

### Lecture 16: NP-Completeness II
- Cook-Levin theorem (SAT is NP-complete)
- Reductions: 3-SAT → Clique, Clique → Vertex Cover
- NP-hard, NP-complete, NP-intermediate
- Coping with NP-hardness: approximation, heuristics, parameterized algorithms

### Lecture 17: Algorithms for DNA Sequence Matching
- Pattern matching: naive, KMP
- Suffix trees and suffix arrays
- Sequence alignment: Needleman-Wunsch, Smith-Waterman
- Applications in bioinformatics

## Time Allocation

| Unit | Lectures | Recommended Hours |
|------|----------|-------------------|
| Intro & Complexity | 3 | 12 |
| Sorting | 4 | 16 |
| Hashing | 2 | 8 |
| Graphs | 4 | 16 |
| Dynamic Programming | 2 | 8 |
| Advanced Topics | 3 | 12 |
| **Total** | **18** | **~72** |
