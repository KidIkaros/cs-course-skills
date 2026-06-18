# CS 161 - Problem Sets

---

## Problem Set 1: Complexity & Divide and Conquer

### Problem 1: Asymptotic Ranking
Rank the following functions from smallest to largest asymptotically. For functions f(n) and g(n), state whether f=O(g), f=Ω(g), or f=Θ(g).

- f₁(n) = n²
- f₂(n) = n² log n
- f₃(n) = 2ⁿ
- f₄(n) = n log n
- f₅(n) = √n
- f₆(n) = log² n

**Answer:** √n < log² n < n log n < n² < n² log n < 2ⁿ

### Problem 2: Closest Pair
Given n points in a plane, describe a divide-and-conquer algorithm to find the closest pair of points in O(n log n) time.

**Solution:**
1. Sort points by x-coordinate
2. Divide into left/right halves
3. Recursively find closest pair in each half (δ = min(dL, dR))
4. Consider strip of width δ around dividing line
5. Sort strip by y-coordinate, compare each point to next 7 points
6. Return minimum distance

### Problem 3: Counting Inversions
An inversion is a pair (i, j) where i < j but A[i] > A[j]. Design an algorithm to count inversions in O(n log n) time.

**Hint:** Modify merge sort. Count inversions during the merge step when elements from the right half are placed before elements from the left half.

---

## Problem Set 2: Dynamic Programming

### Problem 4: Longest Increasing Subsequence
Given an array A[1..n], find the length of the longest strictly increasing subsequence.

**Recurrence:** dp[i] = max(dp[j] + 1) for all j < i where A[j] < A[i]

**Time:** O(n²), or O(n log n) with patience sorting

### Problem 5: Edit Distance
Given strings A[1..m] and B[1..n], find the minimum number of insertions, deletions, and substitutions to transform A into B.

**Recurrence:**
```
dp[i][j] = min(
    dp[i-1][j] + 1,      // delete
    dp[i][j-1] + 1,      // insert
    dp[i-1][j-1] + cost   // substitute (cost=0 if A[i]==B[j], else 1)
)
```

### Problem 6: 0/1 Knapsack
Given n items with weights w[i] and values v[i], and capacity W, maximize total value without exceeding capacity.

**Recurrence:**
```
dp[i][w] = max(
    dp[i-1][w],           // don't take item i
    dp[i-1][w-w[i]] + v[i]  // take item i
)
```

**Time:** O(nW), **Space:** O(nW) → O(W) with rolling array

---

## Problem Set 3: Greedy Algorithms

### Problem 7: Activity Selection
Given n activities with start times s[i] and finish times f[i], find the maximum number of non-overlapping activities.

**Greedy Strategy:** Sort by finish time. Select activity if its start time ≥ last selected finish time.

**Proof (Exchange Argument):** Any optimal solution can be transformed to the greedy solution by swapping activities that conflict with the greedy choice.

### Problem 8: Huffman Coding
Given characters with frequencies, build an optimal prefix-free binary code.

**Algorithm:**
1. Create leaf nodes for each character with frequency
2. Insert into min-priority queue
3. While >1 node: extract two min, create internal node with combined frequency, insert back
4. Tree encodes: left=0, right=1

**Proof:** Greedy choice (merge two least frequent) is optimal because any optimal code must have the two least frequent characters at maximum depth.

---

## Problem Set 4: Graph Algorithms

### Problem 9: Cycle Detection
Design an algorithm to detect if a directed graph has a cycle.

**Solution:** Run DFS. If a back edge is found (edge to an ancestor in DFS tree), the graph has a cycle. Time: O(V + E).

### Problem 10: Topological Sort
Given a DAG, find a linear ordering of vertices such that for every edge (u,v), u comes before v.

**Algorithm:** Run DFS, output vertices in reverse order of finish time. Time: O(V + E).

### Problem 11: Dijkstra's Algorithm
Trace Dijkstra's algorithm on the following weighted graph starting from vertex A:

```
A --4-- B --2-- C
|       |       |
1       5       1
|       |       |
D --3-- E --1-- F
```

**Solution:**
1. Start A: dist[A]=0, others=∞
2. Visit A: dist[B]=4, dist[D]=1
3. Visit D: dist[E]=4
4. Visit B: dist[C]=6
5. Visit E: dist[F]=5
6. Visit F: no updates
7. Visit C: no updates

Final: A=0, B=4, C=6, D=1, E=4, F=5

---

## Problem Set 5: Amortized Analysis & Hashing

### Problem 12: Dynamic Array Amortized Analysis
Using the accounting method, prove that append operations on a dynamic array (that doubles when full) have O(1) amortized cost.

**Solution:** Charge 3 credits per append:
- 1 credit for the actual insert
- 1 credit to eventually move this element when array doubles
- 1 credit to move another element

When array doubles (n elements), we have n credits saved. Doubling costs 2n to copy. We have n credits from past operations + n credits from current operations = 2n. Amortized cost = 3 = O(1).

### Problem 13: Universal Hashing
Show that the family h_{a,b}(x) = ((ax + b) mod p) mod m is universal for prime p > m.

**Proof:** For x ≠ y, we need Pr[h(x) = h(y)] ≤ 1/m.
- h(x) = h(y) ⟹ (ax + b) ≡ (ay + b) (mod p) or differs by p
- a(x-y) ≡ 0 (mod p) only when a ≡ 0 (mod p/(gcd(x-y, p)))
- Since p is prime and x ≠ y: gcd(x-y, p) = 1
- So a(x-y) ≡ 0 only when a ≡ 0 (mod p)
- Probability a ≡ 0 (mod p) among p choices = 1/p < 1/m (since p > m)

---

## Solutions Tips

1. **Always prove correctness** for greedy algorithms using exchange arguments
2. **For DP:** Identify subproblems, prove optimal substructure, define recurrence clearly
3. **For divide-and-conquer:** Prove base case, assume for smaller inputs, show combination
4. **For graph algorithms:** State edge classifications and traversal order
5. **For amortized analysis:** Define potential function and show each operation maintains bound
