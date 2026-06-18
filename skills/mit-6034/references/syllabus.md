# MIT 6.034 — Syllabus & Topic Breakdown

## Week 1: Introduction and Search

| Lecture | Topic | Concepts |
|---------|-------|----------|
| 1 | Course overview, AI as science | Agents, rationality, PEA system |
| 2 | Search: Problem formulation | States, actions, goal test, path cost |
| 3 | Search algorithms | BFS, DFS, hill climbing, beam search |

### Key Topics
- Problem formulation as (S, A, T, G, c)
- Uninformed search: breadth-first, depth-first, uniform-cost
- Informed search: greedy best-first, A* (admissible heuristics)
- Hill climbing and local search
- Branch and bound

## Week 2: Advanced Search and Rule-Based Systems

| Lecture | Topic | Concepts |
|---------|-------|----------|
| 4 | Search continued | Minimax, alpha-beta pruning |
| 5 | Games and optimization | Simulated annealing, genetic algorithms |
| 6 | Rule-based systems | Forward chaining, backward chaining |

### Key Topics
- Minimax with alpha-beta pruning
- Simulated annealing (probability of accepting worse states)
- Genetic algorithms (encoding, crossover, mutation)
- Forward chaining (data-driven)
- Backward chaining (goal-driven)
- Conflict resolution strategies

## Week 3: Constraint Satisfaction and Knowledge Representation

| Lecture | Topic | Concepts |
|---------|-------|----------|
| 7 | Constraint satisfaction | CSP formulation, arc consistency |
| 8 | CSP algorithms | Backtracking, forward checking, min-conflicts |
| 9 | Knowledge representation | Semantic nets, frames, inheritance |

### Key Topics
- CSP as (variables, domains, constraints)
- Arc consistency (AC-3)
- Backtracking with forward checking
- Variable/value ordering heuristics
- Min-conflicts local search for CSPs
- Semantic networks and inheritance hierarchies

## Week 4: Logic and Planning

| Lecture | Topic | Concepts |
|---------|-------|----------|
| 10 | Logic | Propositional logic, entailment, resolution |
| 11 | Planning | STRIPS, situation calculus |
| 12 | Advanced planning | Partial-order planning, graph plan |

### Key Topics
- Propositional logic: syntax, semantics, entailment
- Resolution and refutation
- STRIPS representation (preconditions, effects)
- Situation calculus and the frame problem
- Partial-order planning (POP)
- Planning as search

## Week 5: Probability and Bayesian Networks

| Lecture | Topic | Concepts |
|---------|-------|----------|
| 13 | Probability review | Joint distributions, marginalization, conditioning |
| 14 | Bayes' rule | Prior, likelihood, posterior, naive Bayes |
| 15 | Bayesian networks | Structure, conditional independence, inference |

### Key Topics
- Axioms of probability
- Joint probability distributions
- Bayes' rule: P(H|E) = P(E|H)P(H)/P(E)
- Naive Bayes classifier
- Bayesian network representation
- Conditional independence assumptions
- Exact inference: variable elimination
- Approximate inference: sampling methods

## Week 6: Markov Models and Decision Theory

| Lecture | Topic | Concepts |
|---------|-------|----------|
| 16 | Markov models | Markov chains, HMMs, Viterbi |
| 17 | Decision theory | Utility functions, decision networks |
| 18 | Information gathering | Value of information, optimal decisions |

### Key Topics
- Markov property and Markov chains
- Hidden Markov Models (HMMs)
- Viterbi algorithm (most likely state sequence)
- Forward algorithm (filtering)
- Expected utility and rational decisions
- Decision networks (influence diagrams)
- Value of information

## Week 7: Machine Learning — kNN and Decision Trees

| Lecture | Topic | Concepts |
|---------|-------|----------|
| 19 | k-Nearest neighbors | Distance metrics, weighted voting, curse of dimensionality |
| 20 | Decision trees | ID3, information gain, entropy |
| 21 | Decision trees continued | Continuous attributes, overfitting, pruning |

### Key Topics
- Instance-based learning
- Distance metrics (Euclidean, Hamming, edit distance)
- k-NN with weighted voting
- ID3 algorithm
- Information gain and entropy: H(X) = -Σ p(x) log p(x)
- Gain ratio, Gini index
- Overfitting and pruning strategies

## Week 8: Neural Networks and Backpropagation

| Lecture | Topic | Concepts |
|---------|-------|----------|
| 22 | Neural networks | Perceptrons, linear separability |
| 23 | Backpropagation | Gradient descent, multi-layer networks |
| 24 | Deep learning | Modern architectures, regularization |

### Key Topics
- Perceptron learning rule
- Limitations of single-layer perceptrons (XOR problem)
- Multi-layer networks and activation functions
- Backpropagation algorithm
- Gradient descent (batch, stochastic, mini-batch)
- Regularization (dropout, weight decay)
- Deep learning concepts

## Week 9: Boosting and Kernel Methods

| Lecture | Topic | Concepts |
|---------|-------|----------|
| 25 | Boosting | AdaBoost, weak learners, ensemble methods |
| 26 | Support vector machines | Margin, kernels, feature spaces |
| 27 | Course review | Integration of all topics |

### Key Topics
- Weak learners and strong learners
- AdaBoost algorithm
- Margin maximization
- Support vector machines
- Kernel trick (RBF, polynomial kernels)
- Feature spaces and the kernel perceptron

## Week 10: Vision, Interpretation, and Course Wrap-Up

| Lecture | Topic | Concepts |
|---------|-------|----------|
| 28 | Computer vision | Object recognition, convolutional nets |
| 29 | Semantic interpretation | Parsing, natural language understanding |
| 30 | Course review and future of AI | Ethics, AGI, course synthesis |

### Key Topics
- Visual recognition pipeline
- Convolutional neural networks (CNNs)
- Scene understanding and object detection
- Natural language parsing
- Knowledge representation for interpretation
- AI ethics and future directions
