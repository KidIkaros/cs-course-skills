# CS 221 Syllabus — Topic Breakdown

## Module 1: Intelligent Agents & Problem Formulation

- **Agent types**: reflex, model-based, goal-based, utility-based
- **PEAS**: Performance, Environment, Actuators, Sensors
- **Environment properties**: observable, deterministic, static, discrete, single/multi-agent
- **Problem formulation**: initial state, actions, transition model, goal test, path cost
- **Uninformed search**: BFS, DFS, uniform-cost, iterative deepening
- **Heuristic search**: greedy best-first, A*, heuristic design & admissibility

**Key reference**: Russell & Norvig Ch. 2–4

---

## Module 2: Adversarial Search & Game Playing

- **Deterministic games**: minimax theorem, zero-sum formulation
- **Minimax algorithm**: optimal play with alternating moves
- **Alpha-beta pruning**: early cutoff optimization
- **Expectimax**: stochastic outcomes, chance nodes
- **Evaluation functions**: feature-based approximate minimax
- **Monte Carlo Tree Search (MCTS)**: simulation-based planning

**Key reference**: Russell & Norvig Ch. 5

---

## Module 3: Constraint Satisfaction Problems

- **CSP formulation**: variables, domains, constraints
- **Backtracking search**: depth-first with constraint checking
- **Filtering**: forward checking, arc consistency (AC-3)
- **Ordering**: MRV heuristic, degree heuristic
- **Local search**: min-conflicts, simulated annealing
- **Problem decomposition**: tree decomposition for structured CSPs

**Key reference**: Russell & Norvig Ch. 6

---

## Module 4: Markov Decision Processes

- **MDP definition**: states, actions, transitions, rewards, discount factor γ
- **Bellman equation**: recursive value decomposition
- **Value iteration**: iterative computation of V*
- **Policy iteration**: evaluate → improve → repeat
- **Partially Observable MDPs (POMDPs)**: belief states
- **Reinforcement learning**: model-free methods (Q-learning, SARSA)
- **Function approximation**: tile coding, neural networks for RL

**Key reference**: Russell & Norvig Ch. 16–17, 21–22

---

## Module 5: Machine Learning

- **Supervised learning**: regression, classification
- **Linear regression**: closed-form, gradient descent
- **Logistic regression**: sigmoid, cross-entropy loss
- **Generalization**: bias-variance tradeoff, regularization
- **Neural networks**: perceptrons, backpropagation, architectures
- **Support vector machines**: margin, kernels
- **Decision trees**: ID3, pruning, random forests
- **Unsupervised learning**: k-means, PCA, EM algorithm
- **Evaluation**: precision, recall, F1, ROC/AUC, cross-validation

**Key reference**: Russell & Norvig Ch. 18–20

---

## Module 6: Probabilistic Models

- **Bayesian networks**: DAG representation, conditional independence
- **Inference**: exact (variable elimination, junction tree), approximate (sampling)
- **Markov models**: Markov chains, Hidden Markov Models (HMMs)
- **Inference in HMMs**: forward-backward algorithm, Viterbi
- **Particle filtering**: sequential Monte Carlo for tracking
- **Graphical models**: undirected models (MRFs), factor graphs

**Key reference**: Russell & Norvig Ch. 12–15

---

## Module 7: Logic & Knowledge Representation

- **Propositional logic**: syntax, semantics, entailment
- **Inference**: resolution, DPLL algorithm
- **First-order logic (FOL)**: predicates, quantifiers, unification
- **Resolution in FOL**: Skolemization, inference rules
- **Planning**: STRIPS, PDDL, forward/backward search
- **Situation calculus**: representing and reasoning about change

**Key reference**: Russell & Norvig Ch. 7–10

---

## Module 8: Advanced Topics

- **Natural language processing**: language models, parsing, attention
- **Computer vision**: CNNs, object detection, segmentation
- **Robotics**: localization, SLAM, motion planning
- **Ethics in AI**: bias, fairness, transparency, safety
- **Large language models**: transformers, in-context learning, alignment

**Key reference**: Russell & Norvig Ch. 23–27

---

## Assessment Breakdown (Typical)

| Component | Weight |
|-----------|--------|
| Homework (5–6 sets) | 30% |
| Projects (3–4) | 40% |
| Midterm | 15% |
| Final | 15% |
