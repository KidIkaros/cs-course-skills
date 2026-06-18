# CS 229 — Problem Sets & Practice

Practice problems organized by topic. Solutions available on the [course website](https://cs229.stanford.edu/).

---

## Problem Set 1: Linear Regression & Gradient Descent

1. **Normal equation derivation:** Prove that the gradient of $J(\theta) = \frac{1}{2}(X\theta - y)^T(X\theta - y)$ with respect to $\theta$ is $\nabla_\theta J = X^T(X\theta - y)$. Show that setting this to zero yields the normal equation.

2. **Locally weighted regression:** Given the weight matrix $W$ with $w^{(i)} = \exp\left(-\frac{\|x^{(i)}-x\|^2}{2\tau^2}\right)$, derive the normal equation for the weighted least squares problem. What happens as $\tau \to 0$? As $\tau \to \infty$?

3. **Gradient descent convergence:** For the convex cost function $J(\theta)$ of linear regression with learning rate $\alpha$, prove that $J(\theta^{(t+1)}) \leq J(\theta^{(t)})$ when $\alpha$ is sufficiently small. What is the condition on $\alpha$?

4. **Overfitting vs regularization:** You fit a 10th-degree polynomial to 15 data points and get zero training error. Explain why this is likely overfitting. How would L2 regularization address this? Write the regularized cost function.

---

## Problem Set 2: Logistic Regression & GLMs

1. **Sigmoid derivative:** Prove that if $g(z) = \frac{1}{1+e^{-z}}$, then $g'(z) = g(z)(1-g(z))$.

2. **MLE for logistic regression:** Derive the gradient of the log-likelihood $\ell(\theta)$ for logistic regression. Show that the update rule is $\theta := \theta + \alpha \sum_i (y^{(i)} - h_\theta(x^{(i)}))x^{(i)}$.

3. **Newton's method:** Apply Newton's method to find the root of $f(z) = z^3 - 2z + 2$. Start from $z_0 = 0$ and perform 3 iterations. Compare with gradient descent.

4. **Exponential family:** Show that the Bernoulli distribution belongs to the exponential family. Identify $\eta$, $T(y)$, $b(y)$, and $a(\eta)$.

5. **GDA vs logistic regression:** Under what conditions does GDA produce the same decision boundary as logistic regression? What if the class covariances $\Sigma_0$ and $\Sigma_1$ are different?

---

## Problem Set 3: SVMs & Kernels

1. **Margin derivation:** For the SVM with margin constraint $y^{(i)}(w^Tx^{(i)}+b) \geq 1$, show that the geometric margin is $\gamma = \frac{1}{\|w\|}$.

2. **Dual formulation:** Derive the dual of the soft-margin SVM primal problem:
$$\min_{w,b} \frac{1}{2}\|w\|^2 + C\sum_i \xi_i$$
Show that $w = \sum_i \alpha_i y^{(i)} x^{(i)}$ and that the dual only depends on inner products.

3. **Kernel validity:** Is $K(x,z) = \cos(x^Tz)$ a valid kernel? Justify using Mercer's theorem by checking if the Gram matrix is PSD for a small example.

4. **Kernel computation:** Given two 2D vectors $x = (1,2)^T$ and $z = (3,1)^T$:
   - Compute $K(x,z)$ for a polynomial kernel with $c=1, d=2$
   - Compute $K(x,z)$ for an RBF kernel with $\sigma=1$
   - What is the dimension of the feature space for the polynomial kernel?

5. **Support vectors:** In a trained SVM, what happens to the decision boundary if you remove a training point that is NOT a support vector? What if you remove a support vector?

---

## Problem Set 4: Clustering & EM

1. **K-means convergence:** Prove that the K-means algorithm monotonically decreases the objective $J = \sum_k \sum_{x_i \in C_k} \|x_i - \mu_k\|^2$ at each iteration.

2. **K-means limitations:** Generate a 2D dataset where K-means with $K=2$ fails to find the correct clusters. Explain why and suggest an alternative.

3. **EM for GMM derivation:** Starting from the complete-data log-likelihood for a GMM, derive the E-step and M-step update equations. Show that the M-step reduces to weighted MLE.

4. **EM lower bound:** Prove that the E-step of EM maximizes the ELBO with respect to $q(z)$ while holding $\theta$ fixed. What is the optimal $q(z)$?

5. **Choosing K:** You run K-means for $K=1,...,10$ and get the following objectives: $J = [500, 300, 150, 120, 115, 112, 110, 109, 108.5, 108]$. Using the elbow method, what value of $K$ would you choose? Justify.

---

## Problem Set 5: PCA & Dimensionality Reduction

1. **PCA derivation:** Derive PCA as the solution to the variance maximization problem:
$$\max_u \frac{1}{m}\sum_{i=1}^m (u^T x^{(i)})^2 \quad \text{s.t.} \quad \|u\|=1$$
Show that the solution is the top eigenvector of $\Sigma = \frac{1}{m}\sum_i x^{(i)}(x^{(i)})^T$.

2. **PCA reconstruction error:** Prove that PCA minimizes the average squared reconstruction error:
$$\min_{U: U^TU=I_k} \sum_{i=1}^m \|x^{(i)} - UU^Tx^{(i)}\|^2$$

3. **PCA with SVD:** If $X$ is the centered data matrix and $X = U\Sigma V^T$ is its SVD, express the principal components, projected data, and reconstruction in terms of $U$, $\Sigma$, and $V$.

4. **Choosing components:** You run PCA on a dataset with 20 features. The eigenvalues are: $[4.2, 3.1, 2.0, 1.5, 0.8, 0.5, 0.3, 0.2, 0.1, 0.05, 0.03, 0.02, 0.01, 0.01, 0.005, 0.003, 0.002, 0.001, 0.0005, 0.0001]$. How many components would you keep to explain 90% of variance?

5. **Whitening:** Define PCA whitening as $x_{\text{white}} = \Lambda^{-1/2}U^T(x - \mu)$. Show that the covariance of the whitened data is the identity matrix.

---

## Problem Set 6: Reinforcement Learning

1. **Bellman equation:** For a 3-state MDP with transition probabilities and rewards given in a table, compute $V^\pi$ for a uniform random policy. Then perform one step of policy iteration.

2. **Value iteration:** Implement value iteration for a grid-world MDP (4x4 grid, goal state with reward +1, obstacles with reward -0.1). Run for 20 iterations and plot the value function.

3. **Q-learning:** You have the following Q-table for a 2-state, 2-action MDP:

| | $a=0$ | $a=1$ |
|---|---|---|
| $s=0$ | 0.5 | 0.8 |
| $s=1$ | 0.3 | 0.6 |

Given: $s=0, a=1, r=1, s'=1$. With $\alpha=0.1, \gamma=0.9$, update $Q(s,a)$.

4. **SARSA vs Q-learning:** In a cliff-walking environment, explain why SARSA learns a safer policy than Q-learning. Which has lower expected cost during learning? Which converges to a better policy?

5. **Convergence:** Prove that the Bellman operator $T$ defined by $(TV)(s) = \max_a \sum_{s'} P(s'|s,a)[R(s,a,s') + \gamma V(s')]$ is a $\gamma$-contraction in the $\ell_\infty$ norm.

---

## Exam-Style Questions

### Midterm Questions
1. Derive the complete EM algorithm for a mixture of Gaussians with full covariance matrices.
2. Prove that the SVM dual is a convex optimization problem.
3. Show that PCA is equivalent to finding the best rank-$k$ approximation to $X$ in the Frobenius norm.

### Final Questions
1. Compare and contrast generative and discriminative approaches. Give conditions under which each is preferred.
2. Derive the policy gradient theorem for REINFORCE. How does baseline subtraction reduce variance?
3. Prove the PAC learning bound: for a finite hypothesis class $H$ with $|H|$ hypotheses, after $m \geq \frac{1}{\epsilon}(\log|H| + \log\frac{1}{\delta})$ examples, with probability $\geq 1-\delta$, all $\epsilon$-bad hypotheses are eliminated.

---

## Coding Assignments (Suggested)

1. **Linear regression from scratch:** Implement linear regression using only NumPy. Test on Boston Housing dataset. Compare with scikit-learn.

2. **Logistic regression with Newton's method:** Implement logistic regression. Compare convergence of gradient ascent vs Newton's method on a 2D classification problem.

3. **SVM with kernels:** Implement a kernel SVM (using cvxpy or manual SMO). Visualize decision boundaries for linear, polynomial, and RBF kernels.

4. **K-means and EM:** Implement K-means and EM for GMMs from scratch. Apply to the old faithful geyser dataset. Compare clusterings.

5. **PCA:** Implement PCA. Apply to MNIST digits (first 1000 samples). Visualize first 2 principal components. Reconstruct images with varying numbers of components.

6. **Q-learning:** Implement Q-learning for a simple grid world. Visualize the learned Q-values and policy.

---

## Solutions Framework

For self-study, verify your solutions by:
1. Checking dimensions at each step
2. Verifying edge cases (e.g., $\sigma \to 0$, $C \to \infty$)
3. Running numerical experiments in Python
4. Comparing with scikit-learn implementations
5. Checking convergence guarantees are satisfied
