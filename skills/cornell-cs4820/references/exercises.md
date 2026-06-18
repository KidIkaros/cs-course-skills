# Algorithm Design and Analysis Exercises

## Greedy Algorithms

1. **Interval Scheduling**: Given n intervals [s_i, f_i), find the maximum-size subset of mutually compatible intervals. Prove your greedy strategy is optimal.

2. **Huffman Coding**: Prove that Huffman's algorithm produces an optimal prefix-free code. What happens when symbols have non-integer frequencies?

3. **Scheduling to Minimize Lateness**: Jobs have deadlines d_i and processing times t_i. Prove that Earliest Deadline First minimizes maximum lateness.

4. **Fractional Knapsack**: Show that the greedy approach (by value-to-weight ratio) is optimal for the fractional version. Why doesn't it work for 0/1 knapsack?

5. **Matroid Intersection**: Given two matroids M₁ = (S, I₁) and M₂ = (S, I₂), find the maximum set in I₁ ∩ I₂. Design an algorithm for the intersection of a graphic matroid and a partition matroid.

## Divide and Conquer

6. **Closest Pair**: Given n points in 2D, find the closest pair in O(n log n) time. Prove that the strip-checking step only needs to compare against at most 7 (or 15 in 3D) neighbors.

7. **Median of Medians**: Design a linear-time selection algorithm. Why can't we just recursively partition around a random element? Analyze worst-case vs. expected-case.

8. **Inversions**: Count the number of inversions in an array in O(n log n) time using a modified merge sort.

9. **Karatsuba Multiplication**: Implement the O(n^{1.585}) multiplication algorithm. Compare experimentally with grade-school multiplication for large integers.

10. **Strassen's Algorithm**: Verify that Strassen's 7-multiplication scheme is correct. What is the constant factor overhead, and when does Strassen become faster in practice?

## Dynamic Programming

11. **Edit Distance**: Given two strings of length m and n, compute the minimum edit distance. Recover the actual sequence of operations. Can you do it in O(min(m,n)) space?

12. **0/1 Knapsack**: Given n items with weights w_i and values v_i, and capacity W, find the maximum-value subset that fits. Analyze time and space.

13. **Matrix Chain Multiplication**: Given matrices A₁ (p₀ × p₁), A₂ (p₁ × p₂), ..., Aₙ (p_{n-1} × pₙ), find the parenthesization that minimizes scalar multiplications. Prove optimal substructure.

14. **Longest Increasing Subsequence**: Find the LIS in O(n log n) time. Prove correctness of the patience-sorting approach.

15. **Coin Change**: Given coin denominations, find the minimum number of coins to make change for amount V. When does greedy fail? Design a DP solution.

16. **Viterbi Algorithm**: Implement the Viterbi algorithm for a hidden Markov model. Prove it finds the most probable state sequence.

17. **Parenthesization for Boolean Expression**: Given a boolean expression with variables and operators (AND, OR, XOR), count the number of ways to parenthesize it to get TRUE. Do the same for FALSE.

## Network Flow

18. **Max Flow Construction**: Given a flow network, find a max flow using Ford-Fulkerson. Prove that the residual graph has no augmenting paths when the algorithm terminates.

19. **Bipartite Matching**: Model the assignment problem as a flow problem. Prove that the max-flow min-cut theorem implies Hall's marriage theorem.

20. **Edge-Disjoint Paths**: Given a directed graph G and two vertices s, t, find the maximum number of edge-disjoint s-t paths. (Menger's theorem)

21. **Project Selection**: Given projects with profits p_i and prerequisites (i requires j), formulate as a min-cut problem to select a maximum-profit subset.

22. **Baseball Elimination**: Given a baseball standings table, determine which teams are mathematically eliminated from winning the division. Model as max flow.

23. **Image Segmentation**: Given an image with pixel affinities to foreground/background, find the minimum-cut segmentation.

## NP-Completeness

24. **SAT to 3-SAT Reduction**: Prove that 3-SAT is NP-complete by reducing SAT to 3-SAT. What happens to the number of clauses?

25. **Vertex Cover NP-hardness**: Prove Vertex Cover is NP-hard by reducing from 3-SAT (or from Independent Set). Show the reduction is polynomial.

26. **Hamiltonian Cycle to TSP**: Reduce Hamiltonian Cycle to TSP. Why is the reverse reduction (TSP to HC) not straightforward?

27. **Subset Sum Reduction**: Reduce 3-SAT to Subset Sum. Describe the construction and prove correctness.

28. **Coping Strategies**: For each of the following NP-hard problems, describe a practical approach: (a) TSP for n=100, (b) Graph Coloring for n=10000, (c) SAT with 1000 variables.

## Approximation Algorithms

29. **Vertex Cover 2-Approx**: Prove that the 2-approximation for Vertex Cover (via maximal matching) is correct. Can you do better with LP relaxation?

30. **Set Cover Greedy**: Prove that the greedy algorithm for Set Cover achieves an H(n) ≈ ln n approximation ratio. What is the lower bound on polynomial-time approximability?

31. **Christofides Algorithm**: Describe Christofides' algorithm for metric TSP. Why is the 3/2 ratio achievable for metric but not general TSP?

32. **Primal-Dual for Set Cover**: Design a primal-dual 2-approximation for Vertex Cover. Can you extend it to Set Cover?

## Local Search

33. **Kernighan-Lin**: Implement the Kernighan-Lin algorithm for graph partitioning. Prove that the potential function strictly decreases at each step.

34. **Simulated Annealing for TSP**: Implement simulated annealing for TSP. Design an appropriate cooling schedule and prove convergence.

35. **Max-Cut Local Search**: For Max-Cut, show that any local optimum of single-vertex moves has value at least m/2 (half the edges).

## Randomized Algorithms

36. **Randomized QuickSort**: Prove that randomized quicksort runs in O(n log n) expected time. What is the probability of the worst case?

37. **Karger's Min-Cut**: Implement Karger's randomized contraction algorithm for min-cut. Analyze the probability of success and how many trials are needed.

38. **Skip Lists**: Analyze the expected height and search time of a skip list. Why is it O(log n) expected?

## Advanced

39. **FPT for Vertex Cover**: Design an FPT algorithm for Vertex Cover parameterized by solution size k. What is the running time?

40. **Streaming Algorithms**: Design a streaming algorithm to estimate the number of distinct elements using O(log n) space. (Flajolet-Martin sketch)
