# MIT 6.006 — Problem Sets & Exercises

## Problem Set 1: Introduction & Asymptotic Analysis

### Problem 1: Asymptotic Growth
Rank the following functions by asymptotic growth rate. For each pair, determine if f = O(g), g = O(f), or neither:
- f₁(n) = n²
- f₂(n) = n³
- f₃(n) = 1.5ⁿ
- f₄(n) = 2^(log₂ n)
- f₅(n) = n^(1/2)

### Problem 2: Insertion Sort Analysis
Prove that Insertion Sort runs in O(n + inv) time, where inv is the number of inversions in the input array.

### Problem 3: Practice Problems
- Implement insertion sort and verify its runtime on random vs sorted input
- Count inversions in an array using merge sort modification

## Problem Set 2: Sorting

### Problem 1: Merge Sort Variations
- Implement merge sort with O(n) auxiliary space
- Implement merge sort that is stable
- Analyze: what happens when you use insertion sort for subarrays of size ≤ k?

### Problem 2: Heapsort
- Implement heapsort using a max-heap
- Prove that building a heap bottom-up is O(n)
- Compare empirically with merge sort and Python's sorted()

### Problem 3: Linear-Time Sorting
- Implement counting sort for integer arrays in range [0, k]
- Implement radix sort using counting sort as subroutine
- When is counting sort preferred over comparison sorts?

## Problem Set 3: Hashing

### Problem 1: Hash Table Implementation
- Implement a hash table with chaining
- Use division method: h(k) = k mod m
- Handle collisions with linked lists
- Analyze load factor and average search time

### Problem 2: Open Addressing
- Implement linear probing and quadratic probing
- Observe cluster formation empirically
- Implement double hashing and compare performance

### Problem 3: Universal Hashing
- Implement a universal hash family: h(k) = ((ak + b) mod p) mod m
- Test uniformity by hashing random keys
- Measure collision rate vs. division method

## Problem Set 4: Graphs

### Problem 1: BFS
- Implement BFS using an adjacency list
- Compute shortest paths from a source vertex
- Find connected components in an undirected graph
- Test bipartiteness using BFS coloring

### Problem 2: DFS
- Implement DFS (recursive and iterative)
- Classify edges as tree, back, forward, or cross
- Implement topological sort using DFS
- Detect cycles in directed graphs

### Problem 3: Shortest Paths
- Implement Dijkstra's algorithm with a min-heap
- Implement Bellman-Ford algorithm
- Detect negative weight cycles
- Compare runtimes on various graph sizes

## Problem Set 5: Dynamic Programming

### Problem 1: Rod Cutting
- Implement rod cutting with memoization
- Implement rod cutting with bottom-up tabulation
- Reconstruct the actual cuts made

### Problem 2: Edit Distance
- Implement edit distance between two strings
- Handle insert, delete, substitute operations
- Reconstruct the alignment (sequence of edits)
- Analyze time and space complexity

### Problem 3: Knapsack
- Implement 0/1 knapsack
- Implement unbounded knapsack
- Reconstruct which items were selected
- Test on small and large instances

## Problem Set 6: NP-Completeness

### Problem 1: Reductions
- Reduce SAT to 3-SAT
- Reduce 3-SAT to CLIQUE
- Reduce CLIQUE to VERTEX COVER
- Show each reduction is polynomial time

### Problem 2: NP Verification
- Write a verifier for SAT (given assignment, check if formula is satisfied)
- Write a verifier for HAMILTONIAN CYCLE
- Implement brute-force SAT solver for small instances

### Problem 3: Practice
- Implement a simple SAT solver using DPLL
- Compare brute-force vs DPLL on random 3-SAT instances
- Experiment with different clause densities

## Implementation Challenges

### Easy
1. Implement merge sort from scratch
2. Build a hash table from scratch
3. BFS shortest path on a grid

### Medium
4. Implement Dijkstra's with a binary heap
5. Solve edit distance and reconstruct alignment
6. Detect cycles in a directed graph

### Hard
7. Implement a suffix array construction algorithm
8. Solve 0/1 knapsack with branch and bound
9. Implement an efficient SAT solver

## Self-Test Checklist

After completing each problem set, verify:
- [ ] All algorithms are implemented correctly
- [ ] Time complexity analysis is included
- [ ] Code handles edge cases (empty input, single element, etc.)
- [ ] Solutions are tested on multiple inputs
- [ ] You can explain why each algorithm works
