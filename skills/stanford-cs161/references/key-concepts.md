# Algorithm Design Paradigms - Cheat Sheet

---

## 1. Divide and Conquer

**Pattern:** Break problem into subproblems, solve recursively, combine solutions.

```
solve(problem):
    if base_case: return trivial_solution
    sub1, sub2 = divide(problem)
    sol1 = solve(sub1)
    sol2 = solve(sub2)
    return combine(sol1, sol2)
```

**When to Use:**
- Problem can be split into independent subproblems
- Subproblems are smaller versions of the original
- Combination step is efficient

**Master Theorem:** T(n) = aT(n/b) + O(nᵈ)
- If d > log_b(a): O(nᵈ)
- If d = log_b(a): O(nᵈ log n)
- If d < log_b(a): O(n^(log_b(a)))

**Classic Problems:**
| Problem | Recurrence | Solution |
|---------|-----------|----------|
| Merge sort | T(n) = 2T(n/2) + n | O(n log n) |
| Binary search | T(n) = T(n/2) + 1 | O(log n) |
| Closest pair | T(n) = 2T(n/2) + n | O(n log n) |
| Strassen's matrix | T(n) = 7T(n/2) + n² | O(n^2.81) |

---

## 2. Dynamic Programming

**Pattern:** Solve subproblems, store results, reuse for overlapping subproblems.

**Requirements:**
1. **Optimal substructure:** Optimal solution contains optimal solutions to subproblems
2. **Overlapping subproblems:** Same subproblems solved repeatedly

**Approaches:**
- **Top-down (memoization):** Recursive with cache
- **Bottom-up (tabulation):** Fill table iteratively

**Steps:**
1. Identify subproblems
2. Define recurrence
3. Determine evaluation order
4. Extract solution (not just value)

**Classic Problems:**
| Problem | Recurrence | Time |
|---------|-----------|------|
| LCS | dp[i][j] = dp[i-1][j-1] + 1 if match | O(mn) |
| Edit distance | dp[i][j] = min(ins, del, sub) | O(mn) |
| 0/1 Knapsack | dp[i][w] = max(include, exclude) | O(nW) |
| Matrix chain | dp[i][j] = min_k(dp[i][k] + dp[k+1][j]) | O(n³) |

---

## 3. Greedy Algorithms

**Pattern:** Make locally optimal choice at each step, hope for global optimum.

**When to Use:**
- Greedy choice property: local optimum leads to global optimum
- Optimal substructure: subproblems are optimal given greedy choice
- Exchange argument: any optimal solution can be transformed to greedy solution

**Proof Technique (Exchange Argument):**
1. Assume optimal solution OPT differs from greedy solution GREEDY
2. Find first point of difference
3. Show exchanging GREEDY's choice for OPT's choice doesn't worsen solution
4. Repeat until OPT = GREEDY

**Classic Problems:**
| Problem | Greedy Strategy | Correct? |
|---------|----------------|----------|
| Activity selection | Earliest finish time | Yes |
| Huffman coding | Merge lowest frequency | Yes |
| Fractional knapsack | Highest value/weight | Yes |
| 0/1 Knapsack | Highest value/weight | **No** (use DP) |

---

## 4. Graph Algorithms

### BFS
- Explores layer by layer
- Shortest paths in unweighted graphs
- Time: O(V + E)

### DFS
- Explores as deep as possible first
- Edge classification: tree, back, forward, cross
- Topological sort, cycle detection, SCC
- Time: O(V + E)

### Minimum Spanning Trees
- **Cut property:** Safe edge crosses minimum-weight cut
- **Cycle property:** Heaviest edge in cycle not in MST
- **Kruskal's:** Sort edges, union-find. O(E log E)
- **Prim's:** Grow tree from vertex, priority queue. O(E log V)

### Shortest Paths
- **Dijkstra's:** Non-negative weights, greedy + PQ. O(E log V)
- **Bellman-Ford:** Handles negative weights. O(VE)
- **Floyd-Warshall:** All-pairs. O(V³)

---

## 5. Amortized Analysis

**Aggregate:** Total cost / n operations = amortized cost per operation.

**Accounting:** Assign amortized cost; prepaid operations build credit.

**Potential Method:** Φ(Dᵢ) = potential of data structure. Ŝᵢ = Sᵢ + Φ(Dᵢ) - Φ(Dᵢ₋₁)

**Classic Amortized Bounds:**
| Operation | Worst Case | Amortized |
|-----------|-----------|-----------|
| Dynamic array push | O(n) | O(1) |
| Union-Find (path compression) | O(log n) | O(α(n)) ≈ O(1) |
| Splay tree access | O(n) | O(log n) |

---

## 6. Randomized Algorithms

**Why Randomize:**
- Avoid worst-case inputs
- Simpler algorithms
- Probabilistic guarantees

**Types:**
- **Las Vegas:** Always correct, expected runtime
- **Monte Carlo:** May be wrong, bounded runtime

**Key Tools:**
- Linearity of expectation
- Indicator random variables
- Chernoff bounds

---

## Complexity Cheat Sheet

```
O(1) < O(log log n) < O(log n) < O(√n) < O(n) < O(n log n) < O(n²) < O(n³) < O(2ⁿ) < O(n!)
```

| Problem | Lower Bound | Best Known |
|---------|-------------|------------|
| Comparison sort | Ω(n log n) | O(n log n) |
| Element distinctness | Ω(n log n) | O(n log n) |
| Integer multiplication | Ω(n) | O(n log n) |
| Matrix multiplication | Ω(n²) | O(n^2.37) |
