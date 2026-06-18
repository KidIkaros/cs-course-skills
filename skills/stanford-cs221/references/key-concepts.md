# CS 221 Key Concepts — AI Cheat Sheet

## Rational Agents

A rational agent selects actions that maximize expected performance given its knowledge.

**PEAS Framework**:
- **P**erformance measure — what defines success
- **E**nvironment — what the agent interacts with
- **A**ctuators — what the agent can do
- **S**ensors — what the agent perceives

**Environment Properties**:
| Property | Meaning |
|----------|---------|
| Observable | Agent receives complete state info |
| Deterministic | Next state fully determined by current state + action |
| Static | Environment doesn't change during deliberation |
| Discrete | Finite number of distinct states/actions |
| Single-agent | Only one agent operates |

---

## Search

### Problem Formulation
- **State space**: set of all reachable states
- **Action model**: S × A → S (deterministic) or S × A → P(S) (stochastic)
- **Goal test**: S → {true, false}
- **Path cost**: c(s, a, s') — cumulative cost

### Algorithm Comparison

| Algorithm | Optimal? | Complete? | Time | Space |
|-----------|----------|-----------|------|-------|
| BFS | Yes (unweighted) | Yes | O(b^d) | O(b^d) |
| DFS | No | No (infinite) | O(b^m) | O(bm) |
| UCS | Yes | Yes | O(b^{⌈C*/ε⌉}) | O(b^{⌈C*/ε⌉}) |
| A* | Yes (admissible h) | Yes | O(b^d) | O(b^d) |
| IDDFS | Yes | Yes | O(b^d) | O(bd) |

Where b = branching factor, d = solution depth, m = max depth

### Heuristics
- **Admissible**: h(n) ≤ h*(n) for all n (never overestimates)
- **Consistent**: h(n) ≤ c(n, a, n') + h(n')
- A* with consistent heuristic expands nodes in non-decreasing cost order

**Common heuristics**:
- Manhattan distance (grid, no obstacles)
- Straight-line distance (geographic)
- Pattern database (precomputed subproblem solutions)

---

## Adversarial Search

### Minimax
- **MAX** player maximizes utility, **MIN** player minimizes it
- V*(s) = max_a min_s' V*(s') for MAX nodes
- V*(s) = min_a max_s' V*(s') for MIN nodes
- Time: O(b^m), Space: O(bm)

### Alpha-Beta Pruning
- α = best value MAX can guarantee along path
- β = best value MIN can guarantee along path
- Prune when α ≥ β
- With perfect move ordering: O(b^{m/2}) — doubles effective depth

### Expectimax
- Chance nodes replace MIN nodes
- V*(s) = Σ_s' P(s'|s,a) · V*(s')
- Used when opponent plays stochastically or suboptimally

### Evaluation Functions
- Linear combination of features: f(s) = w₁x₁ + w₂x₂ + ... + wₙxₙ
- Should correlate with true utility
- Learned from game records (temporal difference learning)

---

## Constraint Satisfaction

### CSP Components
- **Variables** X = {X₁, X₂, ..., Xₙ}
- **Domains** D = {D₁, D₂, ..., Dₙ}
- **Constraints** C = {C₁, C₂, ..., Cₘ} (unary, binary, higher-order)

### Consistency
- **Arc consistency**: for every (X, Y) in constraints, for every x ∈ D_X, ∃ y ∈ D_Y satisfying C(X, Y)
- **AC-3**: O(cd³) — enforce arc consistency iteratively
- **k-consistency**: generalize to k-tuples

### Search Strategies
- **Backtracking**: DFS with variable/value ordering heuristics
- **MRV** (Minimum Remaining Values): pick variable with fewest options
- **Degree heuristic**: break ties by most constrained neighbors
- **LCV** (Least Constraining Value): try values that rule out fewest options for neighbors
- **Min-conflicts**: local search — assign value violating fewest constraints

### Problem Decomposition
- **Tree decomposition**: decompose constraint graph into tree
- **Width**: size of largest cluster minus 1
- **Tree-width**: minimum width over all decompositions
- Dynamic programming on tree decomposition solves CSP in O(n · d^w)

---

## Markov Decision Processes

### MDP Definition
- **States** S, **Actions** A, **Transitions** T(s, a, s'), **Rewards** R(s, a, s'), **Discount** γ

### Value Functions
- **State-value**: V^π(s) = E[Σ γ^t R_t | π, s₀ = s]
- **Action-value**: Q^π(s, a) = E[Σ γ^t R_t | π, s₀ = s, a₀ = a]

### Bellman Equations
```
V*(s) = max_a Σ_s' T(s, a, s') [R(s, a, s') + γ V*(s')]
Q*(s, a) = Σ_s' T(s, a, s') [R(s, a, s') + γ max_a' Q*(s', a')]
```

### Algorithms

| Algorithm | Type | Time | Notes |
|-----------|------|------|-------|
| Value Iteration | Dynamic prog. | O(|S|²|A| per iter) | Converges to V* |
| Policy Iteration | Dynamic prog. | O(|S|³) per iteration | Fewer iterations |
| Q-Learning | Model-free RL | — | Learns Q* directly |
| SARSA | Model-free RL | — | Learns Q^π (on-policy) |

### Convergence
- Value iteration converges when |V_{k+1} - V_k|_∞ < ε
- Convergence rate: O(log(1/ε) / log(1/γ))
- Policy iteration converges in finite steps (each iteration improves)

---

## Machine Learning

### Supervised Learning
- **Input**: training set {(x_i, y_i)}
- **Objective**: find f: X → Y that generalizes
- **Loss**: L(f(x), y) measures prediction error

### Linear Models
- **Linear regression**: L = (y - ŷ)², closed-form via normal equation
- **Logistic regression**: L = -[y log(ŷ) + (1-y) log(1-ŷ)]

### Optimization
- **Gradient descent**: θ ← θ - α∇L(θ)
- **Stochastic GD**: update on mini-batches
- **Learning rate**: controls step size

### Neural Networks
- **Architecture**: input → hidden layers → output
- **Activation**: ReLU, sigmoid, tanh
- **Backpropagation**: chain rule for gradient computation
- **Regularization**: dropout, weight decay, early stopping

### Generalization
- **Bias-variance tradeoff**: total error = bias² + variance + noise
- **Overfitting**: low training error, high test error
- **Underfitting**: high training error, high test error
- **Cross-validation**: k-fold estimate of generalization

### Evaluation Metrics
- **Accuracy**: (TP + TN) / Total
- **Precision**: TP / (TP + FP)
- **Recall**: TP / (TP + FN)
- **F1**: 2 · Precision · Recall / (Precision + Recall)
- **AUC-ROC**: area under receiver operating characteristic curve

---

## Probabilistic Models

### Bayesian Networks
- DAG where nodes = random variables, edges = dependencies
- Joint distribution: P(X₁, ..., Xₙ) = Π P(Xᵢ | Parents(Xᵢ))
- **d-separation**: determines conditional independence from graph structure

### Inference
- **Variable elimination**: sum out variables one at a time
- **Junction tree**: exact inference via message passing
- **Sampling**: Monte Carlo, importance sampling, MCMC

### Hidden Markov Models
- States hidden, observations emitted
- **Forward algorithm**: P(X_t | observations_1:t), O(T · |S|²)
- **Viterbi**: most likely state sequence, O(T · |S|²)
- **Forward-backward**: posterior marginals P(X_t | all observations)

### Particle Filtering
- Sequential Monte Carlo for non-Gaussian, nonlinear systems
- Represent distribution as weighted particles
- Steps: predict → update weights → resample

---

## Logic

### Propositional Logic
- Connectives: ¬, ∧, ∨, →, ↔
- **Entailment**: α ⊨ β iff every model of α is a model of β
- **Satisfiability**: exists assignment making formula true

### Inference Methods
- **Truth table enumeration**: O(2^n) — exponential
- **Resolution**: refutation-complete, CNF conversion required
- **DPLL**: backtracking with unit propagation and pure literal elimination

### First-Order Logic
- **Predicates**: P(x), Q(x, y)
- **Quantifiers**: ∀ (universal), ∃ (existential)
- **Unification**: most general unifier for two expressions
- **Resolution in FOL**: Skolemize → convert to CNF → resolve

### Planning
- **STRIPS**: add/delete lists for action effects
- **PDDL**: standardized planning domain definition language
- **Forward search**: start from initial state, search toward goal
- **Backward search**: start from goal, search backward to initial state
