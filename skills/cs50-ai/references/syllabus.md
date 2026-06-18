# CS50 AI Syllabus - Weekly Breakdown

## Week 1: Search

### Topics
- Graph theory fundamentals
- Breadth-First Search (BFS)
- Depth-First Search (DFS)
- Greedy Best-First Search
- A* Search
- Heuristics and admissibility
- Minimax algorithm
- Alpha-beta pruning

### Concepts
- State space, actions, transition model
- Frontier, explored set
- Uninformed vs informed search
- Optimal vs complete algorithms

### Project: Degrees of Separation
- Implement BFS to find shortest path
- Find degrees of separation between actors
- Work with IMDB movie database

### Project: PageRank
- Model web page importance
- Iterative PageRank algorithm
- Handle dangling nodes and damping factor

---

## Week 2: Knowledge

### Topics
- Propositional logic
- Logical connectives (AND, OR, NOT, IMPLIES, BICONDITIONAL)
- Logical equivalence
- Entailment and inference
- Resolution algorithm
- First-order logic (FOL)
- Universal and existential quantifiers

### Concepts
- Knowledge base (KB)
- Model checking
- Inference rules (Modus Ponens, Resolution)
- CNF (Conjunctive Normal Form)

### Project: Minesweeper AI
- Represent game knowledge in propositional logic
- Use inference to deduce safe cells
- Implement AI that never loses

### Project: Logic Puzzle
- Model complex logical constraints
- Use inference to solve puzzles
- Handle contradictions

---

## Week 3: Uncertainty

### Topics
- Probability theory basics
- Conditional probability
- Bayes' Rule
- Joint probability distributions
- Marginalization
- Independence and conditional independence
- Bayesian Networks
- Sampling (prior, rejection, likelihood weighting)
- Markov Models (Hidden Markov Models)

### Concepts
- Random variables
- Prior/posterior probability
- Bayesian inference
- Conditional probability tables (CPTs)

### Project: Diagnosis
- Build Bayesian Network for medical diagnosis
- Implement probabilistic inference
- Handle uncertain evidence

---

## Week 4: Optimization

### Topics
- Optimization problems
- Local search algorithms
- Hill climbing
- Simulated annealing
- Traveling Salesman Problem (TSP)
- Constraint satisfaction problems (CSPs)
- Backtracking search
- Arc consistency
- Min-conflicts heuristic

### Concepts
- Objective function
- State space vs search space
- Local vs global optima
- Constraints (unary, binary, global)

### Project: Traveling Salesman
- Implement local search for TSP
- Compare hill climbing vs simulated annealing
- Find near-optimal solutions

### Project: Crossword
- Model crossword as CSP
- Implement backtracking with inference
- Handle word and letter constraints

---

## Week 5: Machine Learning

### Topics
- Supervised learning
- Unsupervised learning
- Classification vs regression
- k-Nearest Neighbors (k-NN)
- Naive Bayes classifier
- Support Vector Machines (SVMs)
- Decision trees
- Ensemble methods (random forests, boosting)
- Overfitting and regularization
- Cross-validation

### Concepts
- Training/test split
- Accuracy, precision, recall, F1
- Confusion matrix
- Feature engineering
- Hyperparameter tuning

### Project: Shopping
- Predict online shopper purchases
- Implement k-NN classifier
- Evaluate with accuracy metrics

### Project: Nim Game
- Reinforcement learning with Q-learning
- Explore vs exploit trade-off
- Learn optimal strategy through play

---

## Week 6: Neural Networks

### Topics
- Biological neurons
- Perceptrons
- Multilayer networks
- Activation functions (sigmoid, ReLU, tanh)
- Forward propagation
- Backpropagation
- Gradient descent
- Learning rate
- Convolutional Neural Networks (CNNs)
- Recurrent Neural Networks (RNNs)

### Concepts
- Weights and biases
- Loss functions (cross-entropy, MSE)
- Epochs and batches
- Feature maps and pooling

### Project: Traffic Sign Recognition
- Build CNN for image classification
- Train on German traffic sign dataset
- Achieve high accuracy on test set

---

## Week 7: Language

### Topics
- Natural Language Processing (NLP)
- Tokenization and normalization
- N-gram language models
- Parts of speech tagging
- Dependency parsing
- Context-free grammar (CFG)
- Information retrieval
- TF-IDF and bag of words
- Word embeddings (Word2Vec, GloVe)
- Transformers and attention mechanism

### Concepts
- Corpus and vocabulary
- Perplexity
- Parse trees
- Named Entity Recognition (NER)
- Sentiment analysis

### Project: Dynamic Programming
- Implement word segmentation
- Use dynamic programming for optimization
- Handle ambiguous tokenizations

### Project: Attention
- Build attention-based model
- Understand self-attention
- Implement basic transformer components

---

## Final Tips

1. **Start early** - Each project has significant scope
2. **Read the specs** - Understand requirements before coding
3. **Test incrementally** - Build and test small pieces
4. **Use office hours** - CS50 staff and community are helpful
5. **Check autograder** - Submit to verify your implementation
6. **Document your code** - Future you will thank present you
7. **Understand the theory** - Don't just copy solutions
