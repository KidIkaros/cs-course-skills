# MIT 6.006 — Key Concepts Cheat Sheet

## Complexity Classes

| Class | Definition | Examples |
|-------|-----------|----------|
| **P** | Solvable in polynomial time | Sorting, BFS, shortest paths |
| **NP** | Verifiable in polynomial time | SAT, Clique, Graph Coloring |
| **NP-Complete** | In NP AND NP-hard | 3-SAT, Hamiltonian Cycle, TSP |
| **NP-Hard** | At least as hard as NP-complete | Halting Problem,优化版 of NPC problems |

## Common Growth Rates

```
O(1) < O(log n) < O(√n) < O(n) < O(n log n) < O(n²) < O(n³) < O(2ⁿ) < O(n!)
```

## Sorting Algorithms

| Algorithm | Best | Average | Worst | Space | Stable |
|-----------|------|---------|-------|-------|--------|
| Insertion Sort | O(n) | O(n²) | O(n²) | O(1) | Yes |
| Merge Sort | O(n log n) | O(n log n) | O(n log n) | O(n) | Yes |
| Heapsort | O(n log n) | O(n log n) | O(n log n) | O(1) | No |
| Quicksort | O(n log n) | O(n log n) | O(n²) | O(log n) | No |
| Counting Sort | O(n + k) | O(n + k) | O(n + k) | O(n + k) | Yes |
| Radix Sort | O(d(n + k)) | O(d(n + k)) | O(d(n + k)) | O(n + k) | Yes |

**Lower bound for comparison sorts:** Ω(n log n)

## Graph Algorithms

### BFS
- **Purpose:** Shortest paths in unweighted graphs
- **Data structure:** Queue
- **Time:** O(V + E)
- **Properties:** Level-order traversal, tree edges form BFS tree

### DFS
- **Purpose:** Cycle detection, topological sort, SCCs
- **Data structure:** Stack (or recursion)
- **Time:** O(V + E)
- **Properties:** Timestamps (discovery/finish), edge classification

### Dijkstra's
- **Purpose:** Shortest paths, non-negative weights
- **Data structure:** Min-priority queue
- **Time:** O((V + E) log V) with binary heap
- **Greedy property:** Always process closest unvisited vertex

### Bellman-Ford
- **Purpose:** Shortest paths, handles negative weights
- **Time:** O(VE)
- **Detects:** Negative weight cycles

### DAG Shortest Paths
- **Purpose:** Shortest paths in DAGs
- **Time:** O(V + E)
- **Method:** Process in topological order

## Dynamic Programming Recipe

1. **Identify subproblems** — what smaller inputs solve the bigger problem?
2. **Recurrence relation** — how do subproblems combine?
3. **Base cases** — what are the simplest subproblems?
4. **Compute order** — memoization (top-down) or tabulation (bottom-up)?
5. **Recover solution** — backtrack through the table to reconstruct the answer

### Classic DP Problems

| Problem | Recurrence | Time | Space |
|---------|-----------|------|-------|
| Fibonacci | `F(n) = F(n-1) + F(n-2)` | O(n) | O(1) |
| Rod Cutting | `r(n) = max(p[i] + r(n-i))` | O(n²) | O(n) |
| Edit Distance | `D[i][j] = min(...)` | O(mn) | O(mn) |
| LCS | `L[i][j] = ...` | O(mn) | O(mn) |
| 0/1 Knapsack | `K[i][w] = ...` | O(nW) | O(nW) |

## Hashing

- **Chaining:** Each slot holds a linked list. Load factor α = n/m. Expected O(1 + α).
- **Open Addressing:** All elements in table. Load factor α ≤ 1. Probe sequence.
- **Universal Hashing:** Randomized hash family保证 Expected O(1) per operation.
- **Good hash functions:** Distribute keys uniformly, minimize clustering.

## Reductions

If problem A reduces to problem B (A ≤_p B):
- A is no harder than B
- If B is in P, then A is in P
- If A is NP-hard, then B is NP-hard

**Strategy to prove NP-completeness:**
1. Show the problem is in NP (certificate + polynomial verification)
2. Reduce a known NP-complete problem to it

## Master Theorem

For recurrences of the form T(n) = aT(n/b) + O(n^d):

- If d < log_b(a): T(n) = O(n^(log_b(a)))
- If d = log_b(a): T(n) = O(n^d log n)
- If d > log_b(a): T(n) = O(n^d)

**Example:** Merge sort: T(n) = 2T(n/2) + O(n) → d = 1, log_2(2) = 1 → O(n log n)
