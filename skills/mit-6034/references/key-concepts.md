# MIT 6.034 — Key Concepts Cheat Sheet

## Search Algorithms

| Algorithm | Complete? | Optimal? | Time | Space | Strategy |
|-----------|-----------|----------|------|-------|----------|
| BFS | Yes | Yes (unweighted) | O(b^d) | O(b^d) | Queue |
| DFS | No | No | O(b^m) | O(bm) | Stack |
| Uniform-cost | Yes | Yes | O(b^C*/ε) | O(b^C*/ε) | Priority queue |
| Greedy best-first | No | No | O(b^m) | O(b^m) | h(n) |
| A* | Yes | Yes | O(b^d) | O(b^d) | f(n) = g(n) + h(n) |
| Hill climbing | No | No | O(∞) possible | O(1) | Local moves |
| Simulated annealing | Asymptotic | Asymptotic | — | O(1) | Probabilistic |

**b** = branching factor, **d** = depth of solution, **m** = max depth, **C*** = optimal cost, **ε** = min step cost

### Heuristic Properties
- **Admissible**: h(n) never overestimates → A* is optimal
- **Consistent**: h(n) ≤ c(n, n') + h(n') → A* expands fewer nodes

## Rule-Based Systems

### Forward vs. Backward Chaining
| Property | Forward Chaining | Backward Chaining |
|----------|-----------------|-------------------|
| Direction | Data → Goals | Goals → Data |
| Trigger | New fact matches rule | Goal matches rule head |
| Use case | Monitoring, planning | Diagnostics, query answering |
| Risk | Fires irrelevant rules | May explore irrelevant subgoals |

### Conflict Resolution Strategies
1. Refraction: Don't fire same rule on same facts
2. Priority/ordering: Pick most specific or highest priority rule
3. Recency: Prefer rules matching most recent facts

## Constraint Satisfaction

### Arc Consistency (AC-3)
For every arc (X → Y), remove values from X's domain that have no supporting value in Y's domain.

**Time**: O(ed³) where e = constraints, d = max domain size

### CSP Solving Strategies
| Strategy | Description |
|----------|-------------|
| Backtracking | Try assignments, backtrack on failure |
| Forward checking | After assigning X, prune neighbors' domains |
| AC-3 + backtracking | Maintain arc consistency after each assignment |
| Min-conflicts | Local search: assign value minimizing conflicts |
| Min-conflicts + restarts | Restart when stuck (random or step-limited) |

### Variable Ordering Heuristics
- **MRV** (Minimum Remaining Values): Pick variable with fewest legal values
- **Degree heuristic**: Pick variable involved in most constraints
- **LCV** (Least Constraining Value): Try value that rules out fewest options for neighbors

## Probability

### Bayes' Rule
```
P(H|E) = P(E|H) · P(H) / P(E)
```
- P(H) = prior
- P(E|H) = likelihood
- P(H|E) = posterior
- P(E) = evidence (normalizing constant)

### Naive Bayes
```
P(C|X₁,...,Xₙ) ∝ P(C) · ∏ P(Xᵢ|C)
```
Assumes features are conditionally independent given the class.

### Joint Distribution
- n binary variables → 2ⁿ entries
- Marginalization: P(X) = Σ_y P(X,Y=y)
- Conditioning: P(X|Y=y) = P(X,Y=y) / P(Y=y)

## Bayesian Networks

### Structure
- Directed acyclic graph (DAG)
- Nodes = random variables
- Edges = direct influence
- Each node has conditional probability table (CPT) given parents

### Inference
| Method | Type | Complexity |
|--------|------|------------|
| Variable elimination | Exact | Exponential in treewidth |
| Junction tree | Exact | Exponential in treewidth |
| Direct sampling | Approximate | Slow (rejection) |
| Rejection sampling | Approximate | Wasteful |
| Importance sampling | Approximate | Better than rejection |
| Gibbs sampling | Approximate | MCMC, practical |

## Hidden Markov Models

### Three Core Algorithms
| Algorithm | Purpose | Complexity |
|-----------|---------|------------|
| Forward algorithm | P(Xₜ|e₁:t) — filtering | O(K²T) |
| Viterbi algorithm | argmax P(x₁:t|e₁:t) — most likely path | O(K²T) |
| Forward-backward | P(Xₜ|e₁:T) — smoothing | O(K²T) |

**K** = number of states, **T** = sequence length

## Decision Theory

### Expected Utility
```
EU(a) = Σ_s P(s) · U(a, s)
```
Rational agent maximizes expected utility.

### Value of Information
```
VOI = EU(with info) - EU(without info)
```
Never negative. Guides information-gathering actions.

## Machine Learning

### k-Nearest Neighbors
- Classify by majority vote of k closest training examples
- Distance metrics: Euclidean, Manhattan, Hamming, edit distance
- Weighted kNN: weight by 1/distance
- Curse of dimensionality: distances become meaningless in high dimensions

### Decision Trees (ID3)

**Entropy**: H(X) = -Σ p(xᵢ) log₂ p(xᵢ)

**Information Gain**: Gain(X, A) = H(X) - Σ |Xᵥ|/|X| · H(Xᵥ)

| Attribute Selection | Bias |
|--------------------|------|
| Information gain | Prefer attributes with many values (overfitting risk) |
| Gain ratio | Normalizes by intrinsic information |
| Gini index | Used in CART |

**Overfitting**: Tree memorizes training data. Fix with:
- Pre-pruning (stop early)
- Post-pruning (grow full, then remove branches)

### Neural Networks

**Perceptron**:
```
output = step(Σ wᵢxᵢ + bias)
```
Only learns linearly separable functions (no XOR).

**Multi-layer networks**:
- Hidden layers enable non-linear decision boundaries
- Activation functions: sigmoid, tanh, ReLU
- Universal approximation theorem: one hidden layer can approximate any continuous function

**Backpropagation**:
1. Forward pass: compute outputs and loss
2. Backward pass: compute gradients via chain rule
3. Update weights: w ← w - η · ∂L/∂w

### Boosting (AdaBoost)
1. Initialize equal weights
2. Train weak learner
3. Compute weighted error
4. Compute learner weight: α = ½ ln((1-ε)/ε)
5. Update example weights: misclassified examples get higher weight
6. Repeat for T rounds

**Final classifier**: H(x) = sign(Σ αₜ hₜ(x))

### Support Vector Machines
- Find maximum-margin hyperplane
- Margin = distance between hyperplane and nearest points (support vectors)
- Kernel trick: map to higher-dimensional space without explicit computation
- Common kernels: linear, polynomial, RBF (Gaussian)

## Planning

### STRIPS Representation
- **Actions**: Precondition → Add list, Delete list
- **State**: Set of ground atoms
- **Goal**: Set of atoms (all must be true)

### Planning Strategies
| Strategy | Type |
|----------|------|
| Forward search (progression) | State → state |
| Backward search (regression) | Goal → subgoals |
| Partial-order planning | Partially ordered actions |
| Graphplan | Mutex analysis, backward search on plan graph |

### Situation Calculus
- Actions treated as functions
- Result(action, situation) → new situation
- Frame problem: must explicitly state what doesn't change
