# Key Concepts - CS 7646 Machine Learning for Trading

## 1. Technical Analysis

### Bollinger Bands
Price envelope derived from a simple moving average and standard deviation.

```python
def bollinger_bands(prices, window=20, num_std=2):
    sma = prices.rolling(window=window).mean()
    std = prices.rolling(window=window).std()
    upper = sma + (num_std * std)
    lower = sma - (num_std * std)
    return upper, sma, lower
```

**Interpretation**:
- Price touching upper band → potentially overbought (sell signal)
- Price touching lower band → potentially oversold (buy signal)
- Band width indicates volatility

### Relative Strength Index (RSI)
Momentum oscillator measuring speed and magnitude of price changes.

```python
def compute_rsi(prices, period=14):
    delta = prices.diff()
    gain = delta.where(delta > 0, 0).rolling(window=period).mean()
    loss = (-delta.where(delta < 0, 0)).rolling(window=period).mean()
    rs = gain / loss
    rsi = 100 - (100 / (1 + rs))
    return rsi
```

**Thresholds**:
- RSI > 70 → Overbought
- RSI < 30 → Oversold

### MACD
Trend-following momentum indicator.

```python
def compute_macd(prices, fast=12, slow=26, signal=9):
    ema_fast = prices.ewm(span=fast).mean()
    ema_slow = prices.ewm(span=slow).mean()
    macd_line = ema_fast - ema_slow
    signal_line = macd_line.ewm(span=signal).mean()
    histogram = macd_line - signal_line
    return macd_line, signal_line, histogram
```

**Signals**:
- MACD crosses above signal line → bullish
- MACD crosses below signal line → bearish

---

## 2. k-Nearest Neighbors (kNN)

### Algorithm
1. Store all training examples (features + labels)
2. For a new point, compute distance to all training points
3. Select k closest neighbors
4. Assign class by majority vote

### Distance Metrics
- **Euclidean**: d(p,q) = √Σ(pᵢ - qᵢ)²
- **Manhattan**: d(p,q) = Σ|pᵢ - qᵢ|
- **Minkowski**: d(p,q) = (Σ|pᵢ - qᵢ|^p)^(1/p)

### Choosing k
- **Small k** (e.g., 1): Low bias, high variance (overfitting)
- **Large k** (e.g., 50): High bias, low variance (underfitting)
- Typically use k = √N or cross-validation

### Financial Application
Features: Technical indicators (RSI, MACD, Bollinger Band position)  
Labels: UP (price goes up) or DOWN (price goes down)

---

## 3. Decision Trees

### CART Algorithm (Classification and Regression Trees)

```
function BUILD_TREE(data):
    if all labels same OR no features left:
        return LEAF(majority_label)
    
    best_feature, best_threshold = FIND_BEST_SPLIT(data)
    left_data, right_data = SPLIT(data, best_feature, best_threshold)
    
    return NODE(
        feature = best_feature,
        threshold = best_threshold,
        left = BUILD_TREE(left_data),
        right = BUILD_TREE(right_data)
    )
```

### Splitting Criteria
- **Information Gain** (Entropy-based):
  ```
  Entropy(S) = -Σ pᵢ log₂(pᵢ)
  Information Gain = Entropy(parent) - Σ (|Sᵢ|/|S|) * Entropy(Sᵢ)
  ```

- **Gini Impurity**:
  ```
  Gini(S) = 1 - Σ pᵢ²
  ```

### Overfitting Prevention
- Pre-pruning: max_depth, min_samples_per_leaf
- Post-pruning: cost-complexity pruning

---

## 4. Random Forests

### Bootstrap Aggregating (Bagging)
1. Draw N random samples with replacement from training data
2. Train a decision tree on each sample
3. Aggregate predictions (majority vote for classification)

### Random Feature Selection
At each split, only consider a random subset of features:
- Classification: √(total features)
- Regression: total features / 3

### Out-of-Bag (OOB) Error
Each tree is trained on ~63.2% of data. The remaining ~36.8% (out-of-bag samples) can be used as a validation set without a separate holdout.

### Feature Importance
Measured by:
- Mean decrease in impurity (Gini importance)
- Permutation importance (more reliable)

---

## 5. Support Vector Machines (SVM)

### Maximum Margin Classifier
Find hyperplane that maximizes the margin between classes.

**Optimization Problem**:
```
minimize: (1/2)||w||²
subject to: yᵢ(w·xᵢ + b) ≥ 1 for all i
```

### Kernel Trick
Maps data to higher-dimensional space without explicit computation.

| Kernel | Formula | Use Case |
|--------|---------|----------|
| Linear | K(x,y) = x·y | Linearly separable data |
| RBF (Gaussian) | K(x,y) = exp(-γ||x-y||²) | Non-linear, general purpose |
| Polynomial | K(x,y) = (x·y + c)^d | Polynomial relationships |

### Hyperparameters
- **C**: Regularization (high C = low bias, high variance)
- **γ**: RBF kernel width (high γ = complex boundaries)
- **kernel**: Choice of kernel function

### Support Vector Regression (SVR)
Fits a tube of width ε around the regression function, minimizing error outside the tube.

---

## 6. Ensemble Methods

### AdaBoost
Sequential algorithm that focuses on misclassified examples:

```
function ADABOOST(data, T):
    weights = initialize_uniform(N)
    for t = 1 to T:
        weak_learner = TRAIN(data, weights)
        error = COMPUTE_ERROR(weak_learner, data, weights)
        alpha = 0.5 * ln((1 - error) / error)
        weights = UPDATE_WEIGHTS(weights, alpha, weak_learner)
    return weighted combination of weak_learners
```

**Weight Update**:
- Correctly classified: weight × e^(-α)
- Misclassified: weight × e^(α)

### Gradient Boosting
Sequentially fits residuals (errors) of previous models:
```
F₀(x) = initial prediction
for m = 1 to M:
    residuals = y - F_{m-1}(x)
    h_m(x) = fit tree to residuals
    F_m(x) = F_{m-1}(x) + η * h_m(x)
```

---

## 7. Reinforcement Learning

### Q-Learning
Model-free algorithm learning action values:

```
Q(s, a) ← Q(s, a) + α[r + γ·max_a' Q(s', a') - Q(s, a)]
```

Where:
- **s**: Current state
- **a**: Action taken
- **r**: Reward received
- **s'**: Next state
- **α**: Learning rate (0 < α ≤ 1)
- **γ**: Discount factor (0 ≤ γ < 1)

### Financial Application: Trade Execution
- **State**: Current position, market conditions, time remaining
- **Action**: Number of shares to trade
- **Reward**: Profit minus transaction costs
- **Goal**: Execute large order minimizing market impact

### Epsilon-Greedy Exploration
```
with probability ε: choose random action
with probability 1-ε: choose best action (greedy)
```

---

## 8. Portfolio Optimization

### Markowitz Mean-Variance Optimization

**Objective**: Maximize return for a given level of risk.

```
maximize: wᵀμ - (λ/2) wᵀΣw
subject to: Σwᵢ = 1, wᵢ ≥ 0
```

Where:
- **w**: Portfolio weights vector
- **μ**: Expected returns vector
- **Σ**: Covariance matrix
- **λ**: Risk aversion parameter

### Sharpe Ratio
```
Sharpe = (E[R_p] - R_f) / σ_p
```

Maximized when:
```
w* = Σ⁻¹(μ - R_f·1) / 1ᵀΣ⁻¹(μ - R_f·1)
```

### Efficient Frontier
Set of portfolios offering maximum expected return for each level of risk. Investors choose portfolios on the frontier based on risk tolerance.

---

## 9. Model Evaluation

### Metrics for Classification
| Metric | Formula | When to Use |
|--------|---------|-------------|
| Accuracy | (TP+TN)/(TP+TN+FP+FN) | Balanced classes |
| Precision | TP/(TP+FP) | Cost of false positive high |
| Recall | TP/(TP+FN) | Cost of false negative high |
| F1 | 2·(P·R)/(P+R) | Balance precision/recall |

### Metrics for Regression
| Metric | Formula | Notes |
|--------|---------|-------|
| MSE | Σ(yᵢ-ŷᵢ)²/n | Penalizes large errors |
| MAE | Σ|yᵢ-ŷᵢ|/n | Robust to outliers |
| R² | 1 - SS_res/SS_tot | Proportion of variance explained |

### Walk-Forward Validation
For time series data, always use expanding or sliding window validation:

```
|---train---|--test--|
      |---train---|--test--|
            |---train---|--test--|
```

Never use random cross-validation for financial data (causes look-ahead bias).
