---
name: "cornell-cs4820"
description: "Cornell CS 4820 - Introduction to Analysis of Algorithms. Use when studying algorithm design techniques (greedy, divide-and-conquer, DP, network flow), NP-completeness, approximation algorithms, or computational complexity theory."
compatibility: opencode
metadata:
  university: "Cornell University"
  level: "advanced"
  topics: ["algorithms", "dynamic programming", "NP-completeness", "network flow", "approximation"]
  url: "https://www.cs.cornell.edu/courses/cs4820/2026sp/syllabus/"
---

# Cornell CS 4820 - Introduction to Analysis of Algorithms

Advanced course on algorithm design paradigms and computational complexity. Based on Kleinberg & Tardos *Algorithm Design*.

## When to Use

- Solving algorithm design problems using greedy, DP, divide-and-conquer, or network flow
- Analyzing NP-completeness and reductions
- Designing approximation algorithms for intractable problems
- Proving algorithm correctness via invariants, potential functions, or exchange arguments
- Studying for algorithms qualifying exams or technical interviews

## Core Design Paradigms

### Greedy Algorithms
Build solutions incrementally by making locally optimal choices. Prove correctness via:
- **Exchange argument**: Show swapping a non-greedy choice for a greedy one doesn't worsen the solution
- **Matroid theory**: Greedy works when the problem structure forms a matroid
- **Stays-ahead argument**: Show the greedy solution is never behind an optimal solution at any stage

Key problems: activity selection, Huffman coding, minimum spanning tree, interval scheduling, set cover (approximation)

### Divide and Conquer
Split the problem into subproblems, solve recursively, combine results. Analyze via the Master Theorem:
- T(n) = aT(n/b) + O(n^d)
- If log_b(a) < d: O(n^d)
- If log_b(a) = d: O(n^d log n)
- If log_b(a) > d: O(n^{log_b(a)})

Key problems: merge sort, closest pair, Strassen multiplication, FFT, median finding

### Dynamic Programming
Optimal substructure + overlapping subproblems. Steps:
1. Identify subproblems
2. Define recurrence relation
3. Determine evaluation order (top-down or bottom-up)
4. Recover the solution (not just the value)

Key problems: shortest paths (Bellman-Ford, Floyd-Warshall), knapsack, edit distance, LCS, matrix chain multiplication, Viterbi

### Network Flow
Model problems as flow networks. Use max-flow min-cut theorem.
- **Ford-Fulkerson**: O(E * max_flow) — works with integer capacities
- **Edmonds-Karp**: O(VE^2) — BFS-based augmenting paths
- **Push-relabel**: O(V^2E) or O(V^3)

Applications: bipartite matching, edge-disjoint paths, project selection, baseball elimination, image segmentation

### NP-Completeness
Reduction paradigm: reduce a known NP-complete problem to your problem to prove hardness.
- P: problems solvable in polynomial time
- NP: problems verifiable in polynomial time
- NP-complete: in NP AND NP-hard (every NP problem reduces to it)

Key NP-complete problems: SAT, 3-SAT, Clique, Vertex Cover, Hamiltonian Cycle, TSP, Subset Sum, Partition, Graph Coloring

Reduction strategy:
1. Show your problem is in NP (poly-time verifier)
2. Take a known NP-complete problem X
3. Transform an instance of X to an instance of your problem
4. Show the transformation is polynomial-time
5. Show yes-instances map to yes-instances

### Approximation Algorithms
When NP-hard problems must be solved in practice:
- **Vertex Cover**: 2-approximation via maximal matching
- **Set Cover**: O(log n)-approximation via greedy
- **Metric TSP**: 3/2-approximation via Christofides (or 2-approximation via MST + doubling)
- **Knapsack**: PTAS via dynamic programming on scaled values
- **Linear Programming rounding**: General technique for many problems

Approximation ratio: algorithm achieves within factor α of optimal.

### Local Search
Start with a feasible solution, iteratively improve by local moves.
- **Hill climbing**: Greedy local moves (may get stuck in local optima)
- **Simulated annealing**: Allow uphill moves with decreasing probability
- **Kernighan-Lin**: For graph partitioning, swap pairs of vertices
- Proofs: potential function (monotone decrease), Markov chain analysis

## Prerequisites Refresher

- Discrete math: sets, relations, graph theory, proof techniques (induction, contradiction)
- Data structures: heaps, union-find, balanced BSTs, hash tables
- Probability: linearity of expectation, conditional probability, Chernoff bounds

## References

- [Syllabus](references/syllabus.md) — Full topic breakdown and schedule
- [Key Concepts](references/key-concepts.md) — Algorithm analysis cheat sheet
- [Exercises](references/exercises.md) — Design and analysis problems
- [Resources](references/resources.md) — Textbooks, papers, tools

## See Also

- `stanford-cs161` - Stanford CS 161 - Design and Analysis of Algorithms
- `mit-6006` - MIT 6.006 - Introduction to Algorithms
