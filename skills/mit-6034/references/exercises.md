# MIT 6.034 — Problem Sets and Projects

## Problem Sets (9 total)

### PS1: Search
- Implement BFS, DFS, and A* search
- Compare algorithm performance on maze navigation
- Design admissible heuristics for route-finding problems
- Analyze branching factor and solution depth

### PS2: Rule-Based Systems
- Build a forward-chaining inference engine
- Implement backward-chaining with proof trees
- Design a conflict resolution strategy
- Apply rules to a medical diagnosis domain

### PS3: Constraint Satisfaction
- Solve n-queens using backtracking with forward checking
- Implement arc consistency (AC-3)
- Solve a scheduling CSP with min-conflicts
- Compare MRV vs. random variable ordering

### PS4: Logic and Planning
- Convert natural language to propositional logic
- Implement resolution-based theorem prover
- Write a STRIPS-style planner
- Solve a blocks-world planning problem

### PS5: Probability
- Compute joint distributions for multi-variable problems
- Apply Bayes' rule to diagnostic reasoning
- Build a naive Bayes text classifier
- Compare exact vs. approximate inference

### PS6: Bayesian Networks and HMMs
- Construct Bayesian networks from domain knowledge
- Implement variable elimination for exact inference
- Build an HMM for part-of-speech tagging
- Implement Viterbi algorithm for sequence alignment

### PS7: k-Nearest Neighbors
- Implement kNN classifier with multiple distance metrics
- Experiment with different values of k
- Handle mixed continuous/categorical features
- Analyze curse of dimensionality effects

### PS8: Decision Trees
- Implement ID3 from scratch
- Handle continuous attributes (thresholding)
- Add pruning (pre- and post-pruning)
- Compare information gain vs. gain ratio vs. Gini

### PS9: Neural Networks and Boosting
- Implement single-layer perceptron
- Build multi-layer network with backpropagation
- Implement AdaBoost with decision stumps
- Compare boosting vs. single learner performance

## Programming Project

### Project: Object Recognition
Build a system to classify handwritten digits (MNIST-like data) using multiple techniques:

**Phase 1**: kNN baseline
- Implement kNN with Euclidean distance
- Tune k and analyze confusion matrix

**Phase 2**: Decision tree classifier
- Implement ID3/CART
- Apply pruning to reduce overfitting

**Phase 3**: Neural network
- Implement feedforward network
- Train with backpropagation
- Experiment with architecture (layers, neurons, activation functions)

**Phase 4**: Boosting ensemble
- Combine weak learners with AdaBoost
- Analyze ensemble performance vs. individual classifiers

**Deliverables**:
- Working implementation
- Written report comparing classifier performance
- Analysis of error cases and failure modes

## Recommended Practice Problems

### Search
1. Trace A* on a small graph, listing all nodes expanded
2. Determine if a given heuristic is admissible and consistent
3. Compare hill climbing with random restarts on a landscape

### Constraint Satisfaction
1. Run AC-3 by hand on a small CSP
2. Trace backtracking with forward checking on a 3-SAT problem
3. Find a min-conflicts solution for a 4-queens instance

### Probability
1. Compute posterior given prior and likelihood
2. Build a joint distribution table from conditional probabilities
3. Apply Bayes' rule in a medical testing scenario

### Machine Learning
1. Calculate information gain for a candidate attribute split
2. Trace one round of AdaBoost with sample weights
3. Hand-trace backpropagation on a 2-layer network

## Self-Assessment Checklist

- [ ] Can formulate any problem as a search problem
- [ ] Know when to use BFS vs. DFS vs. A*
- [ ] Can design admissible heuristics for new problems
- [ ] Can implement forward and backward chaining
- [ ] Can set up and solve a CSP
- [ ] Can compute Bayes' rule by hand
- [ ] Can construct a Bayesian network from a description
- [ ] Can trace the Viterbi algorithm
- [ ] Can implement ID3 and explain information gain
- [ ] Can implement backpropagation from scratch
- [ ] Can explain how AdaBoost works
- [ ] Can describe the kernel trick for SVMs
