---
name: "cs50-ai"
description: "Harvard CS50 AI - Introduction to Artificial Intelligence with Python. Use when learning AI fundamentals including search algorithms, logic, optimization, machine learning, neural networks, and NLP. Requires Python knowledge."
compatibility: opencode
metadata:
  university: "Harvard University"
  level: "intermediate"
  topics: ["AI", "search", "logic", "optimization", "machine learning", "neural networks", "NLP"]
  url: "https://cs50.harvard.edu/ai/"
---

# CS50 AI - Introduction to Artificial Intelligence with Python

Harvard's free OpenCourseWare covering AI fundamentals through hands-on Python projects.

## When to Use

- Learning search algorithms (BFS, DFS, A*, minimax)
- Working with knowledge representation and logic (propositional/planning)
- Solving optimization problems (local search, constraint satisfaction)
- Understanding machine learning (supervised, unsupervised, reinforcement)
- Building neural networks from scratch
- Implementing NLP and language models
- Creating game-playing AI agents

## Prerequisites

- Python proficiency (variables, functions, loops, lists, dictionaries)
- Basic data structures knowledge
- No prior AI/ML experience required

## Course Structure (7 Weeks)

| Week | Topic | Project |
|------|-------|---------|
| 1 | Search | Degrees of Separation, PageRank |
| 2 | Knowledge | Minesweeper AI, Logic Puzzle |
| 3 | Uncertainty | Bayesian Network, Diagnosis |
| 4 | Optimization | Traveling Salesman, Crossword |
| 5 | Machine Learning | Shopping, Nim Game |
| 6 | Neural Networks | Traffic Sign Recognition |
| 7 | Language | Dynamic Programming, Attention |

## Quick Reference

### Search Algorithms

```python
# BFS - guarantees shortest path
def bfs(state):
    frontier = Queue()
    explored = set()
    frontier.put(start)
    while not frontier.empty():
        state = frontier.get()
        if state == goal: return solution
        explored.add(state)
        for action in actions(state):
            child = result(state, action)
            if child not in explored and child not in frontier:
                frontier.put(child)

# A* Search - uses heuristic
# f(n) = g(n) + h(n)
# g(n) = cost from start to n
# h(n) = heuristic estimate from n to goal
```

### Knowledge Representation

```python
# Propositional Logic
# AND, OR, NOT, IMPLICATION, BICONDITIONAL
# Convert to CNF for resolution

# First-Order Logic
# Universal (∀) and Existential (∃) quantifiers
# Variables, predicates, functions
```

### Machine Learning

```python
# k-Nearest Neighbors
# Naive Bayes
# Support Vector Machines
# Decision Trees
# Neural Networks (forward/backward propagation)

# Key formula: perceptron update
# w_i = w_i + α(y - ŷ) * x_i
```

### Optimization

```python
# Hill Climbing - local maximum problem
# Simulated Annealing - accept worse moves probabilistically
# Traveling Salesman - nearest neighbor, genetic algorithms

# Constraint Satisfaction
# Backtracking, arc consistency, min-conflicts
```

### NLP & Language

```python
# N-grams: P(word | context)
# Tokenization, stemming, lemmatization
# TF-IDF, bag of words, embeddings
# Attention mechanism, transformers
```

## Projects

1. **Degrees of Separation** - BFS on social network graph
2. **Minesweeper** - logical inference AI
3. **Crossword** - constraint satisfaction
4. **Shopping** - k-NN classifier
5. **Nim** - reinforcement learning
6. **Traffic** - CNN for sign recognition
7. **Parser** - natural language parsing

## Key Libraries

```bash
pip install numpy pandas scikit-learn tensorflow matplotlib
```

## Tips

- Start with the simplest solution that works
- Understand the problem before coding
- Test edge cases thoroughly
- Document your approach and complexity analysis
- Use provided distribution code as a starting point

## See Also

- `cs50x` - Harvard CS50x - Introduction to Computer Science (prerequisite)
- `stanford-cs221` - Stanford CS 221 - Artificial Intelligence: Principles and Techniques
- `mit-6034` - MIT 6.034 - Artificial Intelligence
