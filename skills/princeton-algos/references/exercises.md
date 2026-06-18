# Exercises and Practice - Princeton COS 226

## Programming Assignments

### Part I
1. **Percolation** - Model a percolation system using Union-Find. Determine whether an N-by-N system percolates. (Week 1)
2. **Queues** - Implement a double-ended queue and randomized queue using linked lists or resizing arrays. (Week 2)
3. **Collinear Points** - Find all sets of 4 collinear points in a given set. Fast sorting and geometry. (Week 3)

### Part II
4. **8-Puzzle** - Solve the 8-puzzle problem using A* search with Manhattan priority function. (Week 4)
5. **Kd-Trees** - Implement a 2d-tree for efficient range search and nearest-neighbor search. (Week 5)

### Part III
6. **WordNet** - Analyze a semantic network using BFS and SAP (shortest ancestral path). (Week 6)
7. **Seam Carving** - Content-aware image resizing using dynamic programming. (Week 7)

### Part IV
8. **Baseball Elimination** - Determine team elimination using maxflow-maxcut min theorem. (Week 8)

## Conceptual Exercises

### Union-Find
- Draw the trace of weighted quick-union with path compression for given input
- What is the maximum array access for N union operations on N elements?
- Compare union-find with DFS for connectivity problems

### Sorting
- Why is quicksort preferred over mergesort for most practical applications?
- Show the trace of 3-way string quicksort on a given set of strings
- Implement a priority queue that supports both insert and delete-max in O(log n)

### Graphs
- Find all shortest paths in a DAG using topological sort
- Detect negative cycles using Bellman-Ford
- Find bridges and articulation points in an undirected graph
- Implement cycle detection in directed graphs

### Strings
- Build an R-way trie and support wildcard matching
- Implement LZW compression and decompression
- Given a text and pattern, find all occurrences using KMP
- Build an NFA from a regular expression and simulate it

### Dynamic Programming
- Longest common subsequence of two strings
- Knapsack problem (0/1 and unbounded)
- Matrix chain multiplication
- Edit distance between two strings

## Practice Problems

### Interview-style
1. Given a sorted array, find two numbers that sum to a target (two-pointer technique)
2. Implement a LRU cache using a doubly-linked list and hash table
3. Find the median of two sorted arrays in O(log(min(m,n)))
4. Serialize and deserialize a binary tree
5. Find the longest substring without repeating characters

### Algorithm Design
1. Design an algorithm to find the k-th largest element in a stream
2. Given a matrix of 0s and 1s, find the largest rectangle containing only 1s
3. Implement a randomized select algorithm for order statistics
4. Design a data structure that supports insert, delete, and getRandom in O(1)

## Java Implementation Checklist

For each algorithm, verify you can:
- [ ] Write the implementation from scratch
- [ ] Analyze time and space complexity
- [ ] Identify edge cases and handle them
- [ ] Trace through the algorithm with a small example
- [ ] Explain the algorithm to someone else

## Resources for Practice

- algs4.cs.princeton.edu - Complete Java code for all algorithms
- Princeton COS 226 archived assignments
- LeetCode problems tagged with the relevant algorithm topics
- VisuAlgo (visualgo.net) for algorithm visualization
