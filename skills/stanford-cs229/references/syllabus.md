# CS 229 — Syllabus & Topic Breakdown

Stanford University | Andrew Ng

## Unit I: Supervised Learning

### Lecture 1-2: Introduction & Linear Regression
- What is machine learning? Supervised vs unsupervised learning
- Linear regression: hypothesis class, cost function (squared error)
- Least squares, normal equations: $\theta = (X^TX)^{-1}X^T\vec{y}$
- Gradient descent: batch, stochastic, convergence guarantees
- Locally weighted linear regression

### Lecture 3: Classification & Logistic Regression
- Perceptron algorithm
- Logistic regression: sigmoid function, log-likelihood
- Maximum likelihood estimation for logistic regression
- Gradient ascent for MLE
- Newton's method, Fisher scoring

### Lecture 4: Generalized Linear Models (GLMs)
- Exponential family distributions
- Deriving GLMs: mean, natural parameter, sufficient statistic
- Identity link (linear regression), log link (Poisson), logit link (logistic regression)
- Softmax regression for multi-class

### Lecture 5-6: Generative Algorithms
- Gaussian Discriminant Analysis (GDA)
  - Model: $p(x|y) \sim \mathcal{N}(\mu_y, \Sigma)$
  - MLE for GDA parameters
  - GDA vs logistic regression: when each is better
- Naive Bayes for text classification
- Laplace smoothing

### Lecture 7: Support Vector Machines
- Large margin classifiers
- Functional margin vs geometric margin
- Primal SVM: $\min \frac{1}{2}\|w\|^2$ s.t. $y^{(i)}(w^Tx^{(i)}+b) \geq 1$
- Lagrangian duality, KKT conditions
- Dual SVM, support vectors

### Lecture 8: Kernels
- Kernel trick: $K(x,z) = \phi(x)^T\phi(z)$
- Polynomial kernels: $K(x,z) = (x^Tz + c)^d$
- Gaussian RBF kernels: $K(x,z) = \exp(-\frac{\|x-z\|^2}{2\sigma^2})$
- Mercer's theorem: valid kernels
- Kernelized logistic regression, SVMs

### Lecture 9: Bias-Variance Tradeoff, Model Selection
- Overfitting and regularization
- L2 regularization (ridge regression), L1 regularization (LASSO)
- Cross-validation, leave-one-out
- Model complexity, VC dimension
- Bias-variance decomposition

---

## Unit II: Learning Theory

### Lecture 10-11: Learning Theory
- PAC learning framework
- Finite hypothesis classes: sample complexity bounds
- Hoeffding's inequality
- Union bound → finite hypothesis class generalization bound
- Infinite hypothesis classes, VC dimension
- VC dimension of linear classifiers in $\mathbb{R}^n$ is $n+1$
- Structural Risk Minimization

---

## Unit III: Unsupervised Learning

### Lecture 12: Unsupervised Learning & Clustering
- K-means algorithm
  - Assignment step, update step
  - Objective: $\min \sum_{k=1}^K \sum_{x_i \in C_k} \|x_i - \mu_k\|^2$
  - Convergence guarantees, local optima
- Hierarchical clustering: agglomerative, divisive
- Choosing $K$: elbow method, gap statistic

### Lecture 13: Expectation-Maximization (EM)
- Latent variable models
- EM for Gaussian Mixture Models (GMMs)
  - E-step: compute responsibilities $w_j^{(i)} = p(z^{(i)}=j \mid x^{(i)}; \theta)$
  - M-step: update parameters using weighted MLE
- EM as coordinate ascent on lower bound
- General EM derivation: Jensen's inequality, ELBO
- Mixtures of Bernoullis, other mixture models

### Lecture 14: Principal Component Analysis (PCA)
- Dimensionality reduction motivation
- PCA derivation: maximize variance / minimize reconstruction error
- Eigenvectors of covariance matrix $X^TX$
- Algorithm: center data, compute top-$k$ eigenvectors
- Applications: visualization, compression, noise reduction
- Relationship to SVD: $X = U\Sigma V^T$

### Lecture 15: Independent Component Analysis & Factor Analysis
- Cocktail party problem
- ICA: maximize non-Gaussianity, FastICA algorithm
- Factor analysis: latent factors, noise model
- EM for factor analysis

---

## Unit IV: Reinforcement Learning & Control

### Lecture 16-17: Markov Decision Processes (MDPs)
- Sequential decision making, rewards, returns
- Markov property, state transition probabilities
- Policies, state-value function $V^\pi(s)$, action-value function $Q^\pi(s,a)$
- Bellman equations:
  - $V^\pi(s) = \sum_a \pi(a|s) \sum_{s'} P(s'|s,a)[R(s,a,s') + \gamma V^\pi(s')]$
  - $Q^\pi(s,a) = \sum_{s'} P(s'|s,a)[R(s,a,s') + \gamma \sum_{a'} \pi(a'|s') Q^\pi(s',a')]$

### Lecture 18: Value Iteration & Policy Iteration
- Value iteration: $V_{k+1}(s) = \max_a \sum_{s'} P(s'|s,a)[R(s,a,s') + \gamma V_k(s')]$
- Policy iteration: policy evaluation + policy improvement
- Convergence guarantees (contraction mapping)
- Model-based vs model-free RL

### Lecture 19: Reinforcement Learning
- Temporal difference (TD) learning
- Q-learning (off-policy): $Q(s,a) \leftarrow Q(s,a) + \alpha[r + \gamma \max_{a'} Q(s',a') - Q(s,a)]$
- SARSA (on-policy)
- Exploration vs exploitation: $\epsilon$-greedy, UCB
- Function approximation: linear, neural network

### Lecture 20: Continuous State MDPs
- Linear dynamical systems
- LQR (Linear Quadratic Regulation)
- Discretization approaches
- Value function approximation for continuous states

---

## Summary of Key Algorithms

| Algorithm | Type | Key Idea |
|-----------|------|----------|
| Linear Regression | Supervised | Squared error, closed-form |
| Logistic Regression | Supervised | Log-likelihood, sigmoid |
| GDA | Supervised (generative) | Model $p(x|y)$, Bayes rule |
| SVM | Supervised | Max margin, kernels |
| K-means | Unsupervised | Iterative assignment/update |
| EM | Unsupervised | E-step + M-step on latent vars |
| PCA | Unsupervised | Variance maximization via eigendecomposition |
| Value Iteration | RL | Bellman optimality operator |
| Q-learning | RL | Model-free temporal differences |
