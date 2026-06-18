# CS50 AI - Key Concepts Cheat Sheet

## 1. Search Algorithms

### Graph Search Components
- **State**: Current configuration (node in graph)
- **Action**: Move from one state to another
- **Transition Model**: Result of applying action to state
- **State Space**: All possible states
- **Goal Test**: Check if current state is goal
- **Path Cost**: Sum of step costs

### Algorithm Comparison

| Algorithm | Optimal | Complete | Time | Space |
|-----------|---------|----------|------|-------|
| BFS | Yes | Yes | O(b^d) | O(b^d) |
| DFS | No | No* | O(b^m) | O(bm) |
| UCS | Yes | Yes | O(b^C*/ε) | O(b^C*/ε) |
| A* | Yes** | Yes | O(b^d) | O(b^d) |

*b = branching factor, d = depth of solution, m = max depth, C* = optimal cost*

### Heuristics
- **Admissible**: Never overestimates true cost
- **Consistent**: h(n) ≤ c(n,a,n') + h(n') for all n,a,n'
- Common: Manhattan distance, Euclidean distance, misplaced tiles

### Minimax
- **Maximizer**: Tries to maximize score
- **Minimizer**: Tries to minimize score
- **Alpha**: Best already explored option for maximizer
- **Beta**: Best already explored option for minimizer
- Prune branches that can't affect final decision

---

## 2. Knowledge Representation

### Propositional Logic
- **AND** (∧): Both must be true
- **OR** (∨): At least one true
- **NOT** (¬): Negation
- **IMPLIES** (→): P → Q ≡ ¬P ∨ Q
- **BICONDITIONAL** (↔): P ↔ Q ≡ (P → Q) ∧ (Q → P)

### Inference Rules
- **Modus Ponens**: P → Q, P ∴ Q
- **Modus Tollens**: P → Q, ¬Q ∴ ¬P
- **Resolution**: (P ∨ Q), (¬P ∨ R) ∴ (Q ∨ R)

### First-Order Logic
- **Universal** (∀x): For all x
- **Existential** (∃x): There exists some x
- **Predicates**: Properties or relations
- **Functions**: Map objects to objects

### Knowledge Base Construction
1. Identify what you know
2. Convert to formal logic
3. Use inference to derive new knowledge
4. Query for answers

---

## 3. Probability & Uncertainty

### Core Rules
- **Sum Rule**: P(A) = Σ P(A, B)
- **Product Rule**: P(A, B) = P(A) × P(B|A)
- **Bayes' Rule**: P(A|B) = P(B|A) × P(A) / P(B)

### Bayesian Networks
- Directed acyclic graph (DAG)
- Nodes = random variables
- Edges = direct influence
- Conditional probability tables (CPTs)

### Inference Methods
- **Enumeration**: Sum out variables
- **Variable Elimination**: Efficient summation
- **Sampling**: Approximate inference
  - Prior sampling
  - Rejection sampling
  - Likelihood weighting

### Hidden Markov Models
- Hidden states emit observations
- Markov assumption: current state depends only on previous
- Forward algorithm for inference
- Viterbi for most likely state sequence

---

## 4. Optimization

### Local Search
- **Hill Climbing**: Move to best neighbor
  - Problem: local maxima, plateaus, ridges
- **Simulated Annealing**: Accept worse moves with probability
  - Temperature decreases over time
  - P(accept) = e^(-ΔE/T)

### Constraint Satisfaction Problems (CSPs)
- **Variables**: X₁, X₂, ..., Xₙ
- **Domains**: D₁, D₂, ..., Dₙ
- **Constraints**: Rules on variable combinations

### CSP Algorithms
- **Backtracking**: Try values, undo on failure
- **Arc Consistency**: Remove impossible values
- **Min-Conflicts**: Choose value with fewest conflicts
- **Forward Checking**: Check future variables

### Common Optimizations
- Variable ordering (MRV heuristic)
- Value ordering (least constraining value)
- Constraint propagation

---

## 5. Machine Learning

### Supervised Learning
- **Classification**: Discrete labels
- **Regression**: Continuous values

### Key Algorithms
- **k-NN**: Classify by majority vote of k neighbors
- **Naive Bayes**: P(class|features) = P(features|class) × P(class)
- **SVM**: Find maximum margin hyperplane
- **Decision Trees**: Split on most informative feature

### Evaluation Metrics
- **Accuracy**: (TP + TN) / Total
- **Precision**: TP / (TP + FP)
- **Recall**: TP / (TP + FN)
- **F1**: 2 × (Precision × Recall) / (Precision + Recall)

### Overfitting Prevention
- Cross-validation
- Regularization
- Early stopping
- Ensemble methods

### Reinforcement Learning
- **Agent**: Learns by interacting with environment
- **State, Action, Reward**: RL framework
- **Q-Learning**: Learn action-value function
- **ε-greedy**: Balance exploration vs exploitation
- **Discount Factor** (γ): Weight future rewards

---

## 6. Neural Networks

### Architecture
- **Input Layer**: Features
- **Hidden Layers**: Learn representations
- **Output Layer**: Predictions

### Key Components
- **Weights** (w): Connection strength
- **Bias** (b): Threshold offset
- **Activation**: Introduce non-linearity
  - Sigmoid: σ(z) = 1/(1+e^(-z))
  - ReLU: max(0, z)
  - Tanh: (e^z - e^(-z))/(e^z + e^(-z))

### Training
- **Forward Pass**: Compute prediction
- **Loss Function**: Measure error
  - Cross-entropy: -Σ y·log(ŷ)
  - MSE: Σ(y - ŷ)²
- **Backpropagation**: Compute gradients
- **Gradient Descent**: Update weights
  - w = w - α × ∂L/∂w

### CNNs
- **Convolution**: Feature detection
- **Pooling**: Downsample features
- **Fully Connected**: Classification

---

## 7. Natural Language Processing

### Text Processing
- **Tokenization**: Split text into tokens
- **Stemming**: Reduce to root form (crude)
- **Lemmatization**: Reduce to dictionary form

### Language Models
- **N-grams**: P(word | previous n-1 words)
- **Perplexity**: Measure prediction quality

### Representations
- **Bag of Words**: Word frequency counts
- **TF-IDF**: Weight by importance
- **Word Embeddings**: Dense vectors (Word2Vec)

### Parsing
- **Constituency**: Phrase structure trees
- **Dependency**: Word-to-word relations

### Modern NLP
- **Attention**: Focus on relevant parts
- **Transformers**: Self-attention architecture
- **BERT**: Bidirectional encoder
- **GPT**: Autoregressive decoder

---

## Quick Reference: Python Libraries

```python
# Search & Optimization
import heapq, queue, random

# Machine Learning
from sklearn.neighbors import KNeighborsClassifier
from sklearn.naive_bayes import GaussianNB
from sklearn.svm import SVC
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, precision_score, recall_score

# Neural Networks
import numpy as np
import tensorflow as tf
from tensorflow import keras

# NLP
import nltk
from nltk.tokenize import word_tokenize
from collections import Counter

# Data
import pandas as pd
```
