---
name: "stanford-cs221"
description: "Stanford CS 221 - Artificial Intelligence: Principles and Techniques. Use when learning AI fundamentals including search, machine learning, MDPs, constraint satisfaction, graphical models, and logic."
metadata:
  university: "Stanford University"
  level: "intermediate-advanced"
  topics: ["AI", "search", "machine learning", "MDPs", "constraint satisfaction", "graphical models"]
  url: "https://stanford-cs221.github.io/spring2026/"
---

# Stanford CS 221 - Artificial Intelligence: Principles and Techniques

Stanford's foundational AI course covering core techniques and algorithms that power intelligent systems.

## Course Overview

CS 221 introduces the fundamental concepts and techniques of artificial intelligence. The course balances theoretical understanding with practical implementation, covering search, machine learning, decision-making under uncertainty, and knowledge representation.

## When to Use This Skill

- Studying or reviewing AI fundamentals (search, ML, logic, probabilistic reasoning)
- Implementing classic AI algorithms (A*, minimax, MDPs, CSP solvers)
- Preparing for AI interviews or qualifying exams
- Building AI applications that require principled decision-making
- Understanding the theoretical foundations behind modern AI systems

## Course Structure

| Module | Topic | Core Idea |
|--------|-------|-----------|
| 1 | Intelligent Agents | Rational agents, PEAS framework, environment types |
| 2 | Search | BFS, DFS, A*, iterative deepening, heuristic design |
| 3 | Adversarial Search | Minimax, alpha-beta pruning, expectimax |
| 4 | Constraint Satisfaction | Backtracking, arc consistency, local search |
| 5 | Markov Decision Processes | Value iteration, policy iteration, reinforcement learning |
| 6 | Machine Learning | Linear regression, classification, neural networks |
| 7 | Probabilistic Models | Bayesian networks, hidden Markov models, particle filtering |
| 8 | Logic & Planning | Propositional logic, first-order logic, planning |

## Key Algorithms

### Search
- Breadth-First Search (BFS) — optimal, complete for unweighted graphs
- Uniform-Cost Search — optimal with cost function
- A* Search — optimal with admissible heuristic
- Iterative Deepening — memory-efficient completeness

### Adversarial Search
- Minimax — optimal play in zero-sum games
- Alpha-Beta Pruning — optimization of minimax
- Expectimax — games with chance nodes

### Constraint Satisfaction
- Backtracking Search — systematic exploration
- Arc Consistency (AC-3) — constraint propagation
- Min-Conflicts — local search for CSPs

### Decision Making
- Value Iteration — compute optimal value function
- Policy Iteration — compute optimal policy directly
- Q-Learning — model-free reinforcement learning

### Machine Learning
- Linear/Logistic Regression — gradient descent optimization
- Neural Networks — backpropagation, representation learning
- Support Vector Machines — margin maximization
- Decision Trees — recursive partitioning

### Probabilistic Reasoning
- Bayesian Networks — joint distribution factorization
- Variable Elimination — exact inference
- Particle Filtering — approximate inference for dynamic systems

## Prerequisites

- **CS 106B** — Programming Abstractions (recursion, data structures)
- **CS 103** — Mathematical Foundations of Computing (logic, proofs)
- **CS 109** — Probability for Computer Scientists
- **Math 51** — Linear Algebra and Multivariable Calculus

## Textbook

**Artificial Intelligence: A Modern Approach** (4th Edition)
Stuart Russell & Peter Norvig

The primary reference for the course. Chapters map directly to course modules.

## References

- [references/syllabus.md](references/syllabus.md) — Detailed topic breakdown
- [references/key-concepts.md](references/key-concepts.md) — AI concepts cheat sheet
- [references/exercises.md](references/exercises.md) — Problem sets and projects
- [references/resources.md](references/resources.md) — Additional resources

## See Also

- `cs50-ai` - Harvard CS50 AI - Introduction to Artificial Intelligence with Python
- `mit-6034` - MIT 6.034 - Artificial Intelligence
- `stanford-cs229` - Stanford CS 229 - Machine Learning
