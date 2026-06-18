# Key Concepts - Princeton COS 226

## Complexity Classes

| Class | Description | Examples |
|-------|-------------|----------|
| O(1) | Constant time | Array access, hash table lookup |
| O(log n) | Logarithmic | Binary search, BST operations (balanced) |
| O(n) | Linear | Array scan, BFS/DFS |
| O(n log n) | Linearithmic | Mergesort, quicksort (average), heapsort |
| O(n²) | Quadratic | Selection sort, insertion sort, shellsort |
| O(2ⁿ) | Exponential | Brute-force subsets, recursive Fibonacci |
| O(n!) | Factorial | Permutations |

## Fundamental Algorithms

### Sorting

| Algorithm | Best | Average | Worst | Space | Stable |
|-----------|------|---------|-------|-------|--------|
| Selection Sort | n² | n² | n² | 1 | No |
| Insertion Sort | n | n² | n² | 1 | Yes |
| Shellsort | n log n | n^4/3 | n² | 1 | No |
| Mergesort | n log n | n log n | n log n | n | Yes |
| Quicksort | n log n | n log n | n² | log n | No |
| Heapsort | n log n | n log n | n log n | 1 | No |

### Graph Algorithms

| Algorithm | Purpose | Time | Space |
|-----------|---------|------|-------|
| DFS | Exploration, connectivity | V + E | V |
| BFS | Shortest path (unweighted) | V + E | V |
| Dijkstra's | Shortest path (non-negative weights) | E log V | V |
| Bellman-Ford | Shortest path (negative weights) | VE | V |
| Kruskal's | MST | E log E | V |
| Prim's | MST | E log V | V |
| Topological Sort | DAG ordering | V + E | V |
| Kosaraju's SCC | Strongly connected components | V + E | V |

### String Algorithms

| Algorithm | Purpose | Time |
|-----------|---------|------|
| LSD Radix Sort | Fixed-length string sort | WN |
| MSD Radix Sort | Variable-length string sort | WN |
| KMP | Substring search | N + M |
| Boyer-Moore | Substring search | N + M |
| Rabin-Karp | Substring search | N + M (avg) |
| TST | Symbol table (strings) | log N per char |

## Data Structures

| Structure | Search | Insert | Delete | Ordered? | Space |
|-----------|--------|--------|--------|----------|-------|
| Array | n | n | n | No | n |
| Linked List | n | 1 | 1 | No | n |
| BST (balanced) | log n | log n | log n | Yes | n |
| Hash Table | 1 (avg) | 1 (avg) | 1 (avg) | No | n |
| Binary Heap | n | log n | log n | Partial | n |
| Trie | L | L | L | Yes | N·R |

## Algorithm Design Paradigms

### Divide and Conquer
- Break problem into subproblems, solve recursively, combine
- Examples: mergesort, quicksort, BST operations, closest pair

### Greedy Algorithms
- Make locally optimal choice at each step
- Examples: Kruskal's MST, Prim's MST, Huffman coding, Dijkstra's

### Dynamic Programming
- Solve subproblems once, store results, combine
- Examples: knapsack, longest common subsequence, Bellman-Ford

### Backtracking
- Recursively explore all possibilities, prune invalid branches
- Examples: N-queens, Sudoku solver, permutations

## Key Theorems

- **Master Theorem**: Solves T(n) = aT(n/b) + f(n) for divide-and-conquer recurrences
- **Stability**: Sorting algorithm preserves relative order of equal elements
- **In-place**: Algorithm uses O(1) extra space (or O(log n) for recursion stack)
- **Comparison sort lower bound**: Ω(n log n) for comparison-based sorting
