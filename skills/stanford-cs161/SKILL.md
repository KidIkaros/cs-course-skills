---
name: "stanford-cs161"
description: "Stanford CS 161 - Design and Analysis of Algorithms. Use when studying algorithm design paradigms (divide-and-conquer, DP, greedy), data structures (BSTs, heaps, hash tables), graph algorithms, or amortized analysis."
metadata:
  university: "Stanford University"
  level: "intermediate"
  topics: ["algorithms", "data structures", "dynamic programming", "greedy", "graphs", "complexity"]
  url: "https://stanford-cs161.github.io/winter2026/"
---

# Stanford CS 161 - Design and Analysis of Algorithms

## Course Overview

Intermediate-level course on algorithm design and analysis. Covers the principled study of efficient solutions to combinatorial problems arising in computer science. Emphasizes the ability to identify computational problems, reason about their difficulty, and design efficient solutions using algorithmic paradigms.

**Instructors:** Moses Charikar, Ellen Vitercik (Winter 2026)
**Prerequisites:** CS 106B/X, CS 103, CS 109
**Level:** Intermediate

## When to Use This Skill

Use this skill when:
- Studying algorithm design paradigms (divide-and-conquer, dynamic programming, greedy)
- Working with fundamental data structures (BSTs, heaps, hash tables, Union-Find)
- Analyzing graph algorithms (MST, shortest paths, connectivity)
- Analyzing time/space complexity (worst-case, average-case, amortized)
- Solving recurrences or proving algorithm correctness
- Preparing for algorithm interviews or problem sets

## Core Topics

### 1. Complexity Analysis
- Worst-case, average-case analysis
- Big-O, Big-Omega, Big-Theta notation
- Amortized analysis (aggregate, accounting, potential methods)
- Lower bounds and reductions

### 2. Algorithm Design Paradigms
- **Divide and Conquer:** Recurrences, merge sort, quicksort, closest pair, master theorem
- **Dynamic Programming:** Optimal substructure, overlapping subproblems, memoization vs tabulation
- **Greedy Algorithms:** Exchange arguments, matroids, Huffman coding, activity selection
- **Randomized Algorithms:** Quickselect, randomized BSTs, hashing

### 3. Data Structures
- Binary Search Trees (balanced, rotations)
- Heaps and priority queues
- Hash tables (chaining, open addressing, universal hashing)
- Union-Find (disjoint sets)
- Bloom filters

### 4. Graph Algorithms
- BFS, DFS, topological sort
- Strongly connected components
- Minimum spanning trees (Kruskal's, Prim's)
- Shortest paths (Dijkstra's, Bellman-Ford)
- Network flow

## File Structure

```
stanford-cs161/
├── SKILL.md                    # This file
└── references/
    ├── syllabus.md             # Topic breakdown by week
    ├── key-concepts.md         # Algorithm design paradigms cheat sheet
    ├── exercises.md            # Problem sets with solutions
    └── resources.md            # Textbooks, lectures, tools
```

## Quick Reference

### Common Recurrences
| Recurrence | Solution | Example |
|------------|----------|---------|
| T(n) = 2T(n/2) + O(n) | O(n log n) | Merge sort |
| T(n) = T(n/2) + O(1) | O(log n) | Binary search |
| T(n) = 2T(n/2) + O(1) | O(n) | Tree traversal |
| T(n) = T(n-1) + O(n) | O(n²) | Selection sort |
| T(n) = 2T(n-1) + O(1) | O(2ⁿ) | Tower of Hanoi |

### Complexity Hierarchy
```
O(1) ⊂ O(log n) ⊂ O(√n) ⊂ O(n) ⊂ O(n log n) ⊂ O(n²) ⊂ O(2ⁿ) ⊂ O(n!)
```

### Decision Tree Lower Bounds
- Comparison-based sorting: Ω(n log n)
- Searching in sorted array: Ω(log n)

## See Also

- `mit-6006` - MIT 6.006 - Introduction to Algorithms
- `cornell-cs4820` - Cornell CS 4820 - Introduction to Analysis of Algorithms
