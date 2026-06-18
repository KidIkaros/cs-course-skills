# CS 229 — Key Concepts Cheat Sheet

Math-heavy reference for core ML derivations and algorithms.

---

## 1. Linear Regression

**Hypothesis:** $h_\theta(x) = \theta^T x$

**Cost function (squared error):**
$$J(\theta) = \frac{1}{2m} \sum_{i=1}^m \left( h_\theta(x^{(i)}) - y^{(i)} \right)^2$$

**Normal equation (closed-form):**
$$\theta = (X^T X)^{-1} X^T \vec{y}$$

- $X$ is $m \times n$ design matrix, $\vec{y}$ is $m \times 1$ target vector
- Requires $X^TX$ invertible (or use pseudoinverse)

**Gradient descent:**
$$\theta_j := \theta_j - \alpha \sum_{i=1}^m \left( h_\theta(x^{(i)}) - y^{(i)} \right) x_j^{(i)}$$

Vectorized: $\theta := \theta - \alpha X^T(X\theta - \vec{y})$

**Locally weighted:** Add weight matrix $W$ where $w^{(i)} = \exp\left(-\frac{\|x^{(i)} - x\|^2}{2\tau^2}\right)$:
$$\theta = (X^T W X)^{-1} X^T W \vec{y}$$

---

## 2. Logistic Regression

**Hypothesis:** $h_\theta(x) = g(\theta^T x) = \frac{1}{1 + e^{-\theta^T x}}$

where $g(z) = \frac{1}{1+e^{-z}}$ is the sigmoid function.

**Properties:** $g'(z) = g(z)(1 - g(z))$

**Log-likelihood (MLE):**
$$\ell(\theta) = \sum_{i=1}^m \left[ y^{(i)} \log h_\theta(x^{(i)}) + (1-y^{(i)}) \log(1 - h_\theta(x^{(i)})) \right]$$

**Cost function (negative log-likelihood):**
$$J(\theta) = -\frac{1}{m} \ell(\theta) = -\frac{1}{m} \sum_{i=1}^m \left[ y^{(i)} \log h_\theta(x^{(i)}) + (1-y^{(i)}) \log(1 - h_\theta(x^{(i)})) \right]$$

**Gradient ascent:**
$$\theta_j := \theta_j + \alpha \sum_{i=1}^m \left( y^{(i)} - h_\theta(x^{(i)}) \right) x_j^{(i)}$$

**Newton's method (second-order):**
$$\theta := \theta - H^{-1} \nabla_\theta \ell(\theta)$$
where $H$ is the Hessian of $\ell(\theta)$.

---

## 3. Generalized Linear Models

**Exponential family:**
$$p(y; \eta) = b(y) \exp\left( \eta^T T(y) - a(\eta) \right)$$

| Distribution | $\eta$ | $T(y)$ | $b(y)$ | $a(\eta)$ |
|-------------|--------|---------|---------|-----------|
| Gaussian | $\mu$ | $y$ | $\frac{1}{\sqrt{2\pi}}$ | $\mu^2/2$ |
| Bernoulli | $\log\frac{p}{1-p}$ | $y$ | $1$ | $\log(1+e^\eta)$ |
| Poisson | $\log\lambda$ | $y$ | $\frac{1}{y!}$ | $e^\eta$ |

**Key property:** $E[T(y); \eta] = \nabla_\eta a(\eta)$

**Canonical link GLMs:**
- Linear regression: $E[y|x] = \theta^T x$ (identity link)
- Logistic regression: $\log\frac{p(y=1|x)}{p(y=0|x)} = \theta^T x$ (logit link)

---

## 4. Gaussian Discriminant Analysis

**Model:**
$$y \sim \text{Bernoulli}(\phi)$$
$$x|y=0 \sim \mathcal{N}(\mu_0, \Sigma)$$
$$x|y=1 \sim \mathcal{N}(\mu_1, \Sigma)$$

**MLE estimates:**
$$\phi = \frac{1}{m}\sum_{i=1}^m \mathbf{1}\{y^{(i)}=1\}$$
$$\mu_j = \frac{\sum_{i=1}^m \mathbf{1}\{y^{(i)}=j\} \cdot x^{(i)}}{\sum_{i=1}^m \mathbf{1}\{y^{(i)}=j\}}$$
$$\Sigma = \frac{1}{m}\sum_{i=1}^m (x^{(i)} - \mu_{y^{(i)}})(x^{(i)} - \mu_{y^{(i)}})^T$$

**Decision boundary:** $p(y=1|x) = p(y=0|x)$ → linear in $x$ (when $\Sigma_0 = \Sigma_1$)

**GDA vs Logistic Regression:**
- GDA makes stronger assumptions → smaller sample complexity when correct
- Logistic regression makes fewer assumptions → more robust when GDA assumptions wrong

---

## 5. Support Vector Machines

**Maximum margin classifier:**
$$\min_{w,b} \frac{1}{2}\|w\|^2 \quad \text{s.t.} \quad y^{(i)}(w^Tx^{(i)}+b) \geq 1, \;\forall i$$

**Functional margin:** $\hat{\gamma}^{(i)} = y^{(i)}(w^Tx^{(i)}+b)$

**Geometric margin:** $\gamma^{(i)} = \frac{y^{(i)}(w^Tx^{(i)}+b)}{\|w\|}$

**Lagrangian:**
$$\mathcal{L}(w,b,\alpha) = \frac{1}{2}\|w\|^2 - \sum_{i=1}^m \alpha_i \left[ y^{(i)}(w^Tx^{(i)}+b) - 1 \right]$$

**KKT conditions:**
$$\alpha_i \geq 0, \quad \alpha_i \left[ y^{(i)}(w^Tx^{(i)}+b) - 1 \right] = 0$$

**Dual problem:**
$$\max_\alpha W(\alpha) = \sum_{i=1}^m \alpha_i - \frac{1}{2}\sum_{i,j} \alpha_i \alpha_j y^{(i)} y^{(j)} (x^{(i)})^T x^{(j)}$$
$$\text{s.t.} \quad \alpha_i \geq 0, \quad \sum_{i=1}^m \alpha_i y^{(i)} = 0$$

**Soft margin (C-SVM):**
$$\min_{w,b,\xi} \frac{1}{2}\|w\|^2 + C\sum_{i=1}^m \xi_i$$
$$\text{s.t.} \quad y^{(i)}(w^Tx^{(i)}+b) \geq 1 - \xi_i, \quad \xi_i \geq 0$$

**Primal-dual relationship:** $w = \sum_{i=1}^m \alpha_i y^{(i)} x^{(i)}$

---

## 6. Kernel Methods

**Kernel trick:** Replace $x^{(i)T}x^{(j)}$ with $K(x^{(i)}, x^{(j)}) = \phi(x^{(i)})^T\phi(x^{(j)})$

**Common kernels:**
- **Linear:** $K(x,z) = x^Tz$
- **Polynomial:** $K(x,z) = (x^Tz + c)^d$
- **Gaussian RBF:** $K(x,z) = \exp\left(-\frac{\|x-z\|^2}{2\sigma^2}\right)$

**Mercer's theorem:** $K$ is a valid kernel iff the Gram matrix $K_{ij} = K(x^{(i)}, x^{(j)})$ is positive semi-definite for any training set.

**Kernelized SVM:**
$$\max_\alpha \sum_i \alpha_i - \frac{1}{2}\sum_{i,j} \alpha_i \alpha_j y^{(i)} y^{(j)} K(x^{(i)}, x^{(j)})$$

**Prediction:** $f(x) = \text{sign}\left(\sum_{i=1}^m \alpha_i y^{(i)} K(x^{(i)}, x) + b\right)$

---

## 7. K-Means Clustering

**Objective:** $J(C_1,...,C_K) = \sum_{k=1}^K \sum_{x_i \in C_k} \|x_i - \mu_k\|^2$

**Algorithm (Lloyd's):**
1. Initialize centroids $\mu_1,...,\mu_K$ (random or k-means++)
2. **Assignment:** $c^{(i)} = \arg\min_k \|x^{(i)} - \mu_k\|^2$
3. **Update:** $\mu_k = \frac{\sum_{i=1}^m \mathbf{1}\{c^{(i)}=k\} \cdot x^{(i)}}{\sum_{i=1}^m \mathbf{1}\{c^{(i)}=k\}}$
4. Repeat until convergence

**Properties:** Monotonically decreases $J$, converges in finite steps, but to local minimum.

---

## 8. Expectation-Maximization (EM)

**General EM for latent variables:**
Given $p(x,z;\theta)$, maximize $\ell(\theta) = \sum_i \log \sum_{z^{(i)}} p(x^{(i)}, z^{(i)};\theta)$

**E-step:** Compute $w_j^{(i)} = p(z^{(i)}=j \mid x^{(i)}; \theta)$

**M-step:** Maximize expected complete-data log-likelihood:
$$\theta := \arg\max_\theta \sum_i \sum_j w_j^{(i)} \log p(x^{(i)}, z^{(i)}=j; \theta)$$

**EM for GMM:**
- **E-step:** $w_j^{(i)} = \frac{\pi_j \mathcal{N}(x^{(i)};\mu_j,\Sigma_j)}{\sum_l \pi_l \mathcal{N}(x^{(i)};\mu_l,\Sigma_l)}$
- **M-step:**
  - $\pi_j = \frac{1}{m}\sum_i w_j^{(i)}$
  - $\mu_j = \frac{\sum_i w_j^{(i)} x^{(i)}}{\sum_i w_j^{(i)}}$
  - $\Sigma_j = \frac{\sum_i w_j^{(i)} (x^{(i)}-\mu_j)(x^{(i)}-\mu_j)^T}{\sum_i w_j^{(i)}}$

**Lower bound (ELBO):**
$$\text{ELBO}(\theta, q) = \sum_z q(z) \log \frac{p(x,z;\theta)}{q(z)}$$
EM increases ELBO by alternating E and M steps.

---

## 9. Principal Component Analysis (PCA)

**Goal:** Find $k$-dimensional subspace maximizing variance.

**Derivation:** Maximize $\frac{1}{m}\sum_{i=1}^m \|z^{(i)}\|^2$ s.t. $\|u\| = 1$ where $z^{(i)} = U^T x^{(i)}$

**Solution:** $u$ is the eigenvector of $\Sigma = \frac{1}{m}\sum_{i=1}^m x^{(i)} (x^{(i)})^T$ with largest eigenvalue.

**Algorithm:**
1. Center data: $x^{(i)} \leftarrow x^{(i)} - \mu$
2. Compute covariance: $\Sigma = \frac{1}{m}X^TX$
3. Eigendecompose: $\Sigma = U\Lambda U^T$
4. Take top-$k$ columns of $U$ as projection matrix

**Reconstruction:** $\hat{x} = U_k U_k^T x$ (projects to $k$-dim then back)

**Variance explained:** $\frac{\sum_{j=1}^k \lambda_j}{\sum_{j=1}^n \lambda_j}$

**Relationship to SVD:** If $X = U\Sigma V^T$, then principal components are columns of $V$.

---

## 10. Reinforcement Learning

**Markov Decision Process:** $(S, A, P, R, \gamma)$

**Bellman expectation equation:**
$$V^\pi(s) = \sum_a \pi(a|s) \sum_{s'} P(s'|s,a)[R(s,a,s') + \gamma V^\pi(s')]$$

**Bellman optimality equation:**
$$V^*(s) = \max_a \sum_{s'} P(s'|s,a)[R(s,a,s') + \gamma V^*(s')]$$

**Value iteration:**
$$V_{k+1}(s) = \max_a \sum_{s'} P(s'|s,a)[R(s,a,s') + \gamma V_k(s')]$$

**Policy iteration:**
1. **Policy evaluation:** Solve $V^{\pi_k} = R^{\pi_k} + \gamma P^{\pi_k} V^{\pi_k}$ (iteratively)
2. **Policy improvement:** $\pi_{k+1}(s) = \arg\max_a \sum_{s'} P(s'|s,a)[R(s,a,s') + \gamma V^{\pi_k}(s')]$

**Q-learning:**
$$Q(s,a) \leftarrow Q(s,a) + \alpha \left[ r + \gamma \max_{a'} Q(s',a') - Q(s,a) \right]$$

**Convergence:** Q-learning converges to $Q^*$ with probability 1 if all state-action pairs are visited infinitely often and $\alpha \to 0$ appropriately.

**SARSA (on-policy):**
$$Q(s,a) \leftarrow Q(s,a) + \alpha \left[ r + \gamma Q(s', a') - Q(s,a) \right]$$
where $a'$ is sampled from the current policy.

---

## Quick Reference: Notation

| Symbol | Meaning |
|--------|---------|
| $m$ | Number of training examples |
| $n$ | Number of features |
| $x^{(i)}$ | $i$-th training example (feature vector) |
| $y^{(i)}$ | $i$-th training label |
| $\theta$ | Model parameters |
| $\alpha$ | Learning rate |
| $\lambda$ | Regularization parameter |
| $\gamma$ | Discount factor (RL) |
| $\Sigma$ | Covariance matrix |
| $\phi$ | Basis function / mixing coefficient |
| $\mathcal{N}(\mu, \Sigma)$ | Gaussian distribution |
| $\mathbf{1}\{\cdot\}$ | Indicator function |
