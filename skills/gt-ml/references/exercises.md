# CS 7646 - Exercises and Projects

## Lab 1: Data Manipulation with Pandas

### Objective
Load, clean, and analyze stock price data using NumPy and Pandas.

### Tasks
1. **Load CSV Data**: Read historical stock data into a DataFrame
2. **Handle Missing Values**: Forward-fill, backward-fill, or interpolate missing prices
3. **Rolling Statistics**: Compute 20-day and 50-day moving averages
4. **Data Normalization**: Normalize prices to start at 1.0 for comparison
5. **Resample**: Convert daily data to weekly/monthly

### Starter Code
```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt

def load_data(symbol, start_date, end_date):
    dates = pd.date_range(start_date, end_date)
    df = pd.read_csv(f'data/{symbol}.csv', index_col='Date', parse_dates=True)
    return df.reindex(dates)

def compute_daily_returns(df):
    daily_returns = df.copy()
    daily_returns[1:] = (df[1:] / df[:-1].values) - 1
    daily_returns.iloc[0] = 0
    return daily_returns
```

### Questions
1. What happens when you compute daily returns on a normalized series?
2. Why might you use EMA instead of SMA for short-term trading signals?
3. How do you handle the first value when computing percentage changes?

---

## Lab 2: Technical Indicators

### Objective
Implement Bollinger Bands, RSI, and MACD for stock analysis.

### Tasks
1. **Bollinger Bands**: Plot upper, middle, and lower bands
2. **RSI**: Compute 14-day RSI and identify overbought/oversold periods
3. **MACD**: Plot MACD line, signal line, and histogram
4. **Signal Generation**: Create buy/sell signals based on indicator crossovers

### Starter Code
```python
def bollinger_bands(prices, window=20, num_std=2):
    sma = prices.rolling(window=window).mean()
    std = prices.rolling(window=window).std()
    upper_band = sma + (num_std * std)
    lower_band = sma - (num_std * std)
    return upper_band, sma, lower_band

def rsi(prices, period=14):
    delta = prices.diff()
    gain = (delta.where(delta > 0, 0)).rolling(window=period).mean()
    loss = (-delta.where(delta < 0, 0)).rolling(window=period).mean()
    rs = gain / loss
    return 100 - (100 / (1 + rs))
```

### Visualization
```python
def plot_bollinger(prices, upper, middle, lower):
    fig, ax = plt.subplots(figsize=(12, 6))
    ax.plot(prices.index, prices, label='Price', color='blue')
    ax.plot(prices.index, upper, label='Upper Band', color='red', linestyle='--')
    ax.plot(prices.index, middle, label='SMA(20)', color='green')
    ax.plot(prices.index, lower, label='Lower Band', color='red', linestyle='--')
    ax.fill_between(prices.index, upper, lower, alpha=0.1, color='gray')
    ax.legend()
    plt.show()
```

### Questions
1. During which market conditions do Bollinger Bands provide the most useful signals?
2. How does the RSI period length affect signal sensitivity?
3. What is the significance of MACD histogram zero-crossings?

---

## Lab 3: kNN Trading Signal Classifier

### Objective
Build a kNN classifier that predicts stock direction (UP/DOWN) using technical indicators.

### Tasks
1. **Feature Engineering**: Create features from technical indicators
2. **Label Generation**: Create binary labels (1 = UP, -1 = DOWN)
3. **Train/Test Split**: Use time-based split (not random)
4. **Model Training**: Train kNN with different k values
5. **Evaluation**: Compute accuracy, precision, recall

### Starter Code
```python
from sklearn.neighbors import KNeighborsClassifier

def create_features(prices, window=5):
    df = pd.DataFrame(index=prices.index)
    df['returns'] = prices.pct_change()
    df['sma_ratio'] = prices / prices.rolling(window).mean()
    df['volatility'] = prices.pct_change().rolling(window).std()
    return df.dropna()

def create_labels(prices, threshold=0.0):
    labels = prices.pct_change().shift(-1)
    return (labels > threshold).astype(int)

def train_knn(X_train, y_train, k=5):
    knn = KNeighborsClassifier(n_neighbors=k)
    knn.fit(X_train, y_train)
    return knn
```

### Experimentation
1. Try k = 1, 3, 5, 10, 20 - which works best?
2. Add more features: RSI, MACD histogram, volume change
3. Compare performance on different stocks (AAPL vs. SPY)

---

## Lab 4: Decision Trees and Random Forests

### Objective
Implement and compare single decision trees with random forest ensembles.

### Tasks
1. **Single Tree**: Train and visualize a decision tree
2. **Random Forest**: Train forest with varying number of trees
3. **OOB Error**: Plot OOB error vs. number of trees
4. **Feature Importance**: Identify most predictive features
5. **Comparison**: Single tree vs. random forest accuracy

### Starter Code
```python
from sklearn.tree import DecisionTreeClassifier
from sklearn.ensemble import RandomForestClassifier

def train_decision_tree(X_train, y_train, max_depth=5):
    dt = DecisionTreeClassifier(max_depth=max_depth, random_state=42)
    dt.fit(X_train, y_train)
    return dt

def train_random_forest(X_train, y_train, n_trees=100, max_depth=5):
    rf = RandomForestClassifier(
        n_estimators=n_trees,
        max_depth=max_depth,
        oob_score=True,
        random_state=42
    )
    rf.fit(X_train, y_train)
    return rf

def plot_oob_error(rf, X_test, y_test, n_trees_range):
    oob_errors = []
    test_errors = []
    for n in n_trees_range:
        rf_temp = RandomForestClassifier(n_estimators=n, oob_score=True)
        rf_temp.fit(X_train, y_train)
        oob_errors.append(1 - rf_temp.oob_score_)
        test_errors.append(1 - rf_temp.score(X_test, y_test))
    return oob_errors, test_errors
```

### Questions
1. Why does random forest generally outperform a single decision tree?
2. How does increasing max_depth affect bias and variance?
3. What does the OOB error estimate tell us about model performance?

---

## Lab 5: Boosting and SVM

### Objective
Implement AdaBoost classifier and compare with SVM for stock prediction.

### Tasks
1. **AdaBoost**: Train with different numbers of weak learners
2. **SVM**: Train linear and RBF kernel SVMs
3. **Hyperparameter Tuning**: Grid search for optimal parameters
4. **Performance Comparison**: Compare all ensemble methods

### Starter Code
```python
from sklearn.ensemble import AdaBoostClassifier
from sklearn.svm import SVC
from sklearn.model_selection import GridSearchCV

def train_adaboost(X_train, y_train, n_estimators=50):
    ada = AdaBoostClassifier(
        n_estimators=n_estimators,
        learning_rate=0.1,
        random_state=42
    )
    ada.fit(X_train, y_train)
    return ada

def train_svm(X_train, y_train, kernel='rbf', C=1.0, gamma='scale'):
    svm = SVC(kernel=kernel, C=C, gamma=gamma)
    svm.fit(X_train, y_train)
    return svm

# Hyperparameter tuning
param_grid = {
    'C': [0.1, 1, 10, 100],
    'gamma': ['scale', 'auto', 0.1, 0.01],
    'kernel': ['rbf', 'linear']
}
grid_search = GridSearchCV(SVC(), param_grid, cv=5, scoring='accuracy')
grid_search.fit(X_train, y_train)
```

### Analysis
1. How does AdaBoost's sequential nature differ from random forest's parallel approach?
2. When might SVM outperform tree-based methods?
3. What are the trade-offs between kernel choice and training time?

---

## Lab 6: Regression and Walk-Forward Validation

### Objective
Build regression models for price prediction with proper time-series validation.

### Tasks
1. **Linear Regression**: Predict next-day returns
2. **Regularized Regression**: Implement Ridge and Lasso
3. **Walk-Forward Validation**: Build expanding/sliding window evaluation
4. **Feature Selection**: Use regularization for feature importance

### Starter Code
```python
from sklearn.linear_model import LinearRegression, Ridge, Lasso

def walk_forward_validation(data, model, window=500, step=21):
    predictions = []
    actuals = []
    
    for i in range(window, len(data), step):
        train_start = max(0, i - window)
        X_train = features[train_start:i]
        y_train = labels[train_start:i]
        X_test = features[i:i+step]
        y_test = labels[i:i+step]
        
        model.fit(X_train, y_train)
        preds = model.predict(X_test)
        
        predictions.extend(preds)
        actuals.extend(y_test)
    
    return np.array(predictions), np.array(actuals)
```

### Evaluation
```python
def compute_metrics(actuals, predictions):
    mse = np.mean((actuals - predictions) ** 2)
    mae = np.mean(np.abs(actuals - predictions))
    r2 = 1 - np.sum((actuals - predictions)**2) / np.sum((actuals - np.mean(actuals))**2)
    return {'MSE': mse, 'MAE': mae, 'R²': r2}
```

---

## Lab 7: Reinforcement Learning for Trade Execution

### Objective
Implement Q-learning agent for optimal trade execution.

### Tasks
1. **Environment Design**: Define states, actions, rewards
2. **Q-Table Implementation**: Initialize and update Q-values
3. **Training Loop**: Train agent over multiple episodes
4. **Evaluation**: Compare RL agent vs. rule-based execution

### Starter Code
```python
class TradeEnvironment:
    def __init__(self, prices, shares_to_trade=100):
        self.prices = prices
        self.shares_total = shares_to_trade
        self.reset()
    
    def reset(self):
        self.shares_remaining = self.shares_total
        self.current_step = 0
        return self._get_state()
    
    def _get_state(self):
        price_change = (self.prices[self.current_step] - 
                       self.prices[max(0, self.current_step-1)]) / self.prices[max(0, self.current_step-1)]
        return (self.shares_remaining, round(price_change * 10))
    
    def step(self, action):
        # action = number of shares to trade
        shares_to_trade = min(action, self.shares_remaining)
        reward = -shares_to_trade * self.prices[self.current_step]
        self.shares_remaining -= shares_to_trade
        self.current_step += 1
        done = self.shares_remaining == 0 or self.current_step >= len(self.prices) - 1
        return self._get_state(), reward, done

def q_learning_train(env, episodes=1000, alpha=0.1, gamma=0.9, epsilon=0.1):
    q_table = {}
    
    for episode in range(episodes):
        state = env.reset()
        done = False
        
        while not done:
            if random.random() < epsilon:
                action = random.randint(0, min(10, state[0]))
            else:
                action = get_best_action(q_table, state)
            
            next_state, reward, done = env.step(action)
            
            # Q-value update
            old_q = q_table.get((state, action), 0)
            next_max = max([q_table.get((next_state, a), 0) for a in range(11)])
            q_table[(state, action)] = old_q + alpha * (reward + gamma * next_max - old_q)
            
            state = next_state
    
    return q_table
```

### Comparison Strategies
1. **Naive**: Trade equal amounts each period
2. **TWAP**: Time-weighted average price
3. **RL Agent**: Q-learning optimized execution

---

## Lab 8: Portfolio Optimization

### Objective
Build a portfolio optimizer using mean-variance optimization.

### Tasks
1. **Covariance Matrix**: Compute from historical returns
2. **Efficient Frontier**: Generate by varying risk aversion
3. **Sharpe Maximization**: Find optimal portfolio weights
4. **Visualization**: Plot efficient frontier with individual assets

### Starter Code
```python
from scipy.optimize import minimize

def portfolio_stats(weights, returns_mean, returns_cov):
    port_return = np.sum(returns_mean * weights)
    port_volatility = np.sqrt(np.dot(weights.T, np.dot(returns_cov, weights)))
    sharpe = port_return / port_volatility
    return port_return, port_volatility, sharpe

def optimize_portfolio(returns_mean, returns_cov, risk_aversion=1.0):
    n_assets = len(returns_mean)
    
    def objective(weights):
        port_return, port_volatility, sharpe = portfolio_stats(
            weights, returns_mean, returns_cov
        )
        return -(port_return - (0.5 / risk_aversion) * port_volatility**2)
    
    constraints = ({'type': 'eq', 'fun': lambda x: np.sum(x) - 1})
    bounds = tuple((0, 1) for _ in range(n_assets))
    init_weights = np.array([1/n_assets] * n_assets)
    
    result = minimize(objective, init_weights, method='SLSQP',
                     bounds=bounds, constraints=constraints)
    return result.x

def plot_efficient_frontier(returns_mean, returns_cov, n_portfolios=10000):
    results = np.zeros((n_portfolios, 3))
    for i in range(n_portfolios):
        weights = np.random.dirichlet(np.ones(len(returns_mean)))
        results[i] = portfolio_stats(weights, returns_mean, returns_cov)
    
    plt.scatter(results[:, 1], results[:, 0], c=results[:, 2], cmap='viridis')
    plt.colorbar(label='Sharpe Ratio')
    plt.xlabel('Volatility')
    plt.ylabel('Return')
    plt.show()
```

---

## Final Project Requirements

### Objective
Design and implement a complete trading system using techniques learned throughout the course.

### Requirements
1. **Data Pipeline**: Load, clean, and feature-engineer market data
2. **ML Model**: At least one classifier/regressor for signal generation
3. **Ensemble**: Use bagging, boosting, or random forest
4. **Backtesting**: Walk-forward validation with realistic assumptions
5. **Portfolio**: Position sizing and risk management
6. **Evaluation**: Sharpe ratio, max drawdown, comparison to benchmark

### Deliverables
- Code repository with clear documentation
- Written report (3-5 pages) covering:
  - Strategy description
  - Model selection rationale
  - Backtesting results
  - Risk analysis
  - Conclusions and limitations

### Grading Rubric
| Criterion | Points |
|-----------|--------|
| Code quality and documentation | 20 |
| Strategy soundness | 25 |
| Model implementation | 25 |
| Backtesting rigor | 15 |
| Written report quality | 15 |

---

## Common Pitfalls

1. **Look-Ahead Bias**: Using future information in training
2. **Survivorship Bias**: Only testing on stocks that still exist
3. **Transaction Costs**: Ignoring commissions and slippage
4. **Overfitting**: Optimizing too aggressively on historical data
5. **Regime Change**: Markets change; past performance ≠ future results
