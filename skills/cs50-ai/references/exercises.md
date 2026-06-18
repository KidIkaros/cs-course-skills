# CS50 AI - Practice Problems

## Week 1: Search

### Exercise 1: BFS Implementation
**Goal**: Find shortest path in a maze

```python
# Given a 2D grid:
# 0 = open, 1 = wall, S = start, E = end
# Implement BFS to find shortest path length

def bfs_maze(maze, start, end):
    # Your code here
    # Return: (path_length, path) or (None, None) if no path
    pass
```

**Test cases**:
```python
maze1 = [
    [0, 0, 1, 0],
    [1, 0, 1, 0],
    [0, 0, 0, 0],
    [1, 1, 0, 'E']
]
# Expected: length = 6
```

### Exercise 2: A* Search
**Goal**: Implement A* with Manhattan distance heuristic

```python
def a_star(graph, start, goal, h):
    # graph: dict of {node: [(neighbor, cost), ...]}
    # h: heuristic function
    # Return: (path, cost) or (None, None)
    pass
```

### Exercise 3: Minimax
**Goal**: Implement minimax for Tic-Tac-Toe

```python
def minimax(board, is_maximizing):
    # board: list of 9 cells (X, O, or None)
    # Return: (best_move, score)
    pass
```

---

## Week 2: Knowledge

### Exercise 4: Propositional Logic
**Goal**: Implement basic inference

```python
class LogicKB:
    def __init__(self):
        self.rules = []
    
    def add_rule(self, rule):
        # Add implication: antecedent -> consequent
        pass
    
    def query(self, query):
        # Return True if KB entails query
        pass

# Example usage:
kb = LogicKB()
kb.add_rule(("raining", "wet_ground"))  # If raining, then wet ground
kb.add_rule(("cloudy", "raining"))      # If cloudy, then raining
print(kb.query(("cloudy", "wet_ground")))  # Should be True
```

### Exercise 5: Constraint Satisfaction
**Goal**: Color a map with 4 colors

```python
def graph_coloring(graph, colors):
    # graph: dict of {region: [neighbors]}
    # colors: list of available colors
    # Return: dict of {region: color} or None
    pass

# Test: Australia map
australia = {
    'WA': ['NT', 'SA'],
    'NT': ['WA', 'SA', 'Q'],
    'SA': ['WA', 'NT', 'Q', 'NSW', 'V'],
    'Q': ['NT', 'SA', 'NSW'],
    'NSW': ['Q', 'SA', 'V'],
    'V': ['SA', 'NSW'],
    'T': []
}
```

---

## Week 3: Uncertainty

### Exercise 6: Bayes' Rule
**Goal**: Calculate posterior probability

```python
def bayes_rule(prior, likelihood, evidence):
    # prior: P(H)
    # likelihood: P(E|H)
    # evidence: P(E)
    # Return: P(H|E)
    pass

# Example: Medical test
# P(Disease) = 0.001
# P(Positive|Disease) = 0.99
# P(Positive) = 0.05
# What is P(Disease|Positive)?
```

### Exercise 7: Naive Bayes
**Goal**: Classify text messages as spam/ham

```python
def naive_bayes_train(training_data):
    # training_data: list of (text, label) pairs
    # Return: learned parameters
    pass

def naive_bayes_predict(params, text):
    # Return: predicted label
    pass
```

---

## Week 4: Optimization

### Exercise 8: Hill Climbing
**Goal**: Optimize a function

```python
def hill_climbing(func, neighbors, max_iterations=1000):
    # func: objective function to maximize
    # neighbors: function returning neighboring states
    # Return: (best_state, best_value)
    pass

# Test: Maximize f(x) = -(x-3)^2 + 10
def f(x): return -(x-3)**2 + 10
def get_neighbors(x): return [x-0.1, x+0.1]
```

### Exercise 9: Traveling Salesman
**Goal**: Find near-optimal tour

```python
def tsp_nearest_neighbor(distances):
    # distances: 2D matrix of distances between cities
    # Return: (tour, total_distance)
    pass
```

### Exercise 10: Sudoku Solver
**Goal**: Solve Sudoku using CSP

```python
def solve_sudoku(grid):
    # grid: 9x9 list (0 = empty)
    # Return: solved grid or None
    pass
```

---

## Week 5: Machine Learning

### Exercise 11: k-NN from Scratch
**Goal**: Implement k-Nearest Neighbors

```python
def knn_fit(X_train, y_train):
    # Store training data
    return (X_train, y_train)

def knn_predict(model, X_test, k=3):
    # X_test: new samples
    # Return: predictions
    pass

def euclidean_distance(a, b):
    # Calculate distance between two points
    pass
```

### Exercise 12: Decision Tree
**Goal**: Implement simple decision tree

```python
class DecisionNode:
    def __init__(self, feature=None, threshold=None, left=None, right=None, value=None):
        self.feature = feature
        self.threshold = threshold
        self.left = left
        self.right = right
        self.value = value  # For leaf nodes

def build_tree(X, y):
    # Build decision tree
    # Return: root node
    pass

def predict(tree, x):
    # Predict class for sample x
    pass
```

### Exercise 13: Reinforcement Learning
**Goal**: Q-learning for simple grid world

```python
def q_learning(env, episodes=1000, alpha=0.1, gamma=0.99, epsilon=0.1):
    # env: environment with reset(), step(), observe()
    # Return: Q-table
    pass
```

---

## Week 6: Neural Networks

### Exercise 14: Perceptron
**Goal**: Implement single perceptron

```python
def perceptron(X, y, epochs=100, lr=0.1):
    # X: features (n_samples, n_features)
    # y: labels (0 or 1)
    # Return: weights, bias
    pass

def perceptron_predict(weights, bias, x):
    # Return: prediction (0 or 1)
    pass
```

### Exercise 15: Forward Propagation
**Goal**: Implement forward pass through network

```python
def sigmoid(z):
    return 1 / (1 + np.exp(-z))

def forward_pass(X, weights, biases):
    # weights: list of weight matrices
    # biases: list of bias vectors
    # Return: output, list of activations
    pass
```

### Exercise 16: Backpropagation
**Goal**: Train a simple network

```python
def train_neural_network(X, y, hidden_size=10, epochs=1000, lr=0.1):
    # Initialize weights randomly
    # For each epoch:
    #   Forward pass
    #   Calculate loss
    #   Backward pass (compute gradients)
    #   Update weights
    # Return: trained weights, biases
    pass
```

---

## Week 7: Language

### Exercise 17: N-gram Model
**Goal**: Build language model

```python
def build_ngrams(text, n=2):
    # Return: dict of {context: [next_words]}
    pass

def generate_text(ngrams, seed, length=50):
    # Generate text of given length
    pass
```

### Exercise 18: Text Classification
**Goal**: Sentiment analysis

```python
def bag_of_words(texts):
    # Create vocabulary and feature vectors
    # Return: vocabulary, matrix
    pass

def train_classifier(X, y):
    # Train logistic regression
    pass
```

### Exercise 19: Dynamic Programming
**Goal**: Word segmentation

```python
def segment(text, dictionary):
    # Split text into valid words
    # Use dynamic programming
    # Return: list of words or None
    pass

# Example:
# segment("hellothere", {"hello", "there"}) -> ["hello", "there"]
```

---

## Solutions Framework

For each exercise:
1. Write function signature
2. Add docstring explaining approach
3. Implement solution
4. Write test cases
5. Analyze time/space complexity
6. Consider edge cases

### Complexity Reference
| Algorithm | Time | Space |
|-----------|------|-------|
| BFS | O(V + E) | O(V) |
| DFS | O(V + E) | O(V) |
| A* | O(b^d) | O(b^d) |
| k-NN | O(n·d) | O(n·d) |
| Decision Tree | O(n·log(n)) | O(nodes) |
| Neural Network | O(epochs·n·w) | O(w) |
