# Algorithm Analysis Cheat Sheet

## Complexity Classes

| Class | Definition |
|-------|-----------|
| P | Decidable in O(n^k) time for some constant k |
| NP | Yes-instances verifiable in O(n^k) time |
| NP-hard | At least as hard as every problem in NP |
| NP-complete | In NP AND NP-hard |
| EXP | Decidable in O(2^{n^k}) time |

## Asymptotic Notations

- f(n) = O(g(n)): ∃ c, n₀ such that f(n) ≤ c·g(n) for all n ≥ n₀
- f(n) = Ω(g(n)): ∃ c, n₀ such that f(n) ≥ c·g(n) for all n ≥ n₀
- f(n) = Θ(g(n)): f(n) = O(g(n)) AND f(n) = Ω(g(n))
- f(n) = o(g(n)): lim_{n→∞} f(n)/g(n) = 0

## Master Theorem

For T(n) = aT(n/b) + O(n^d):
- Case 1: log_b(a) > d → T(n) = O(n^{log_b(a)})
- Case 2: log_b(a) = d → T(n) = O(n^d log n)
- Case 3: log_b(a) < d → T(n) = O(n^d)

## Common Recurrences

| Recurrence | Solution | Algorithm |
|-----------|----------|-----------|
| T(n) = 2T(n/2) + O(n) | O(n log n) | Merge sort |
| T(n) = T(n/2) + O(1) | O(log n) | Binary search |
| T(n) = 2T(n/2) + O(1) | O(n) | Tree traversal |
| T(n) = 7T(n/2) + O(n²) | O(n^{log₂7}) ≈ O(n^2.81) | Strassen |
| T(n) = T(n-1) + O(n) | O(n²) | Selection sort |
| T(n) = 2T(n-1) + O(1) | O(2ⁿ) | Recursive Fibonacci |

## Key Algorithm Complexities

| Algorithm | Time | Space | Stable? |
|-----------|------|-------|---------|
| Merge sort | O(n log n) | O(n) | Yes |
| Quick sort | O(n log n) avg | O(log n) | No |
| Heap sort | O(n log n) | O(1) | No |
| Insertion sort | O(n²) | O(1) | Yes |
| BFS/DFS | O(V + E) | O(V) | — |
| Dijkstra | O((V+E) log V) | O(V) | — |
| Bellman-Ford | O(VE) | O(V) | — |
| Floyd-Warshall | O(V³) | O(V²) | — |
| Kruskal/Prim | O(E log V) | O(V) | — |
| Ford-Fulkerson | O(E · max_flow) | O(V+E) | — |
| Edmonds-Karp | O(VE²) | O(V+E) | — |

## Network Flow Theorems

- **Max-Flow Min-Cut**: Max flow = min cut capacity
- **Integrality Theorem**: If capacities are integer, there exists an integer max flow
- **Konig's Theorem**: In bipartite graphs, max matching = min vertex cover

## NP-Complete Reduction Chain

```
SAT → 3-SAT → Vertex Cover → Clique → Independent Set
                                  ↓
                              Hamiltonian Cycle → TSP
Subset Sum → Partition
3-D Matching → 3-Coloring
```

## Approximation Ratios

| Problem | Ratio | Technique |
|---------|-------|-----------|
| Vertex Cover | 2 | Maximal matching |
| Set Cover | H(n) ≈ ln n | Greedy |
| Metric TSP | 2 | MST doubling |
| Metric TSP | 3/2 | Christofides |
| Knapsack | 1+ε | PTAS (DP rounding) |
| MAX-SAT | 7/8 | Randomized rounding |

## Probabilistic Bounds

- **Markov**: P(X ≥ t) ≤ E[X]/t
- **Chebyshev**: P(|X-μ| ≥ t) ≤ σ²/t²
- **Chernoff**: P(X ≥ (1+δ)μ) ≤ e^{-δ²μ/3} for 0 < δ < 1
- **Union Bound**: P(A₁ ∪ ... ∪ Aₙ) ≤ Σ P(Aᵢ)

## Linear Programming Basics

- Primal: max c^T x, Ax ≤ b, x ≥ 0
- Dual: min b^T y, A^T y ≥ c, y ≥ 0
- Strong duality: optimal primal = optimal dual
- Complementary slackness: xᵢ > 0 ⟹ (Ax)ᵢ = bᵢ
- Fractional vertex cover = LP relaxation of vertex cover
