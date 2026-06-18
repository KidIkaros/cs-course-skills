# CS 7646 - Machine Learning for Trading: Syllabus

**University**: Georgia Institute of Technology  
**Instructor**: Prof. Tucker Balch  
**Format**: Free on Udacity  
**URL**: https://www.udacity.com/course/machine-learning-for-trading--ud501

---

## Module 1: Data Manipulation with NumPy and Pandas

**Duration**: ~2 weeks  
**Prerequisites**: Basic Python

### Learning Objectives
- Manipulate financial data using NumPy arrays and Pandas DataFrames
- Handle dates, missing values, and data normalization
- Perform rolling computations and采样

### Topics
- NumPy fundamentals: arrays, slicing, broadcasting, vectorization
- Pandas: Series, DataFrame, indexing, groupby
- Date ranges and time series operations
- Rolling windows and采样
- Data normalization techniques (min-max, z-score)

### Lab
- Analyze stock price data
- Compute rolling statistics
- Normalize and compare securities

---

## Module 2: Technical Analysis of Financial Data

**Duration**: ~2 weeks  
**Prerequisites**: Module 1

### Learning Objectives
- Compute and interpret technical indicators
- Generate trading signals from price and volume data
- Visualize financial data with matplotlib

### Topics
- Bollinger Bands (20-day SMA ± 2σ)
- Moving averages (SMA, EMA)
- Relative Strength Index (RSI)
- MACD (Moving Average Convergence Divergence)
- On-Balance Volume (OBV)

### Lab
- Compute technical indicators for real stock data
- Plot Bollinger Bands and identify trading signals
- Compare indicator performance across different stocks

---

## Module 3: Stock Trading Simulation

**Duration**: ~1 week  
**Prerequisites**: Modules 1-2

### Learning Objectives
- Build and run a trading simulation
- Understand order management (BUY, SELL, HOLD)
- Evaluate strategy performance

### Topics
- Order types and execution
- Portfolio state tracking
- Transaction costs
- Performance metrics (cumulative return, Sharpe ratio)
- Benchmarking against market indices

### Lab
- Implement a basic trading simulation using QSTK
- Execute trades based on technical signals
- Compare strategy returns vs. buy-and-hold

---

## Module 4: Machine Learning Classification - kNN

**Duration**: ~2 weeks  
**Prerequisites**: Module 2

### Learning Objectives
- Understand the k-nearest neighbors algorithm
- Apply kNN to financial signal classification
- Tune hyperparameters for optimal performance

### Topics
- Instance-based learning fundamentals
- Distance metrics (Euclidean, Manhattan, Minkowski)
- Choosing k: bias-variance tradeoff
- Feature engineering for financial data
- Class imbalance in trading (more SELL than BUY signals)

### Lab
- Implement kNN classifier for stock direction prediction
- Experiment with different k values
- Evaluate using accuracy, precision, recall

---

## Module 5: Ensemble Methods - Bagging and Random Forests

**Duration**: ~2 weeks  
**Prerequisites**: Module 4

### Learning Objectives
- Understand ensemble learning principles
- Implement bagging and random forests
- Compare ensemble methods to single classifiers

### Topics
- Bootstrap aggregating (bagging)
- Random feature selection
- Out-of-bag (OOB) error estimation
- Decision tree fundamentals (CART algorithm)
- Information gain and Gini impurity
- Feature importance ranking

### Lab
- Build a random forest classifier for stock prediction
- Compare single tree vs. random forest performance
- Analyze feature importance

---

## Module 6: Boosting and SVMs

**Duration**: ~2 weeks  
**Prerequisites**: Module 5

### Learning Objectives
- Implement AdaBoost and gradient boosting
- Understand support vector machines for classification and regression
- Apply kernel methods for non-linear problems

### Topics
- AdaBoost algorithm
- Gradient boosting
- Support Vector Machines (SVM) theory
- Maximum margin classifiers
- Kernel trick (RBF, polynomial, sigmoid)
- Support Vector Regression (SVR)

### Lab
- Implement AdaBoost for stock direction classification
- Train SVM/SVR models for price prediction
- Compare boosting vs. bagging vs. SVM performance

---

## Module 7: Regression and Model Selection

**Duration**: ~2 weeks  
**Prerequisites**: Modules 4-6

### Learning Objectives
- Apply regression models to financial forecasting
- Select and tune models using cross-validation
- Detect and prevent overfitting

### Topics
- Linear regression
- Multiple regression
- Ridge and Lasso regularization
- Cross-validation (k-fold, walk-forward)
- Overfitting detection and prevention
- Evaluation metrics (MSE, MAE, R²)

### Lab
- Build regression models for stock return prediction
- Use walk-forward validation for time series
- Compare regularized vs. unregularized models

---

## Module 8: Reinforcement Learning

**Duration**: ~2 weeks  
**Prerequisites**: Module 4

### Learning Objectives
- Understand the reinforcement learning framework
- Implement Q-learning for trade execution
- Design reward functions for financial applications

### Topics
- Agent-environment interaction
- States, actions, rewards
- Q-tables and Q-learning algorithm
- Epsilon-greedy exploration
- Discount factors and learning rates
- Policy optimization

### Lab
- Implement Q-learning agent for optimal trade execution
- Design state representations for market data
- Compare RL agent vs. rule-based strategies

---

## Module 9: Portfolio Optimization and Management

**Duration**: ~2 weeks  
**Prerequisites**: All previous modules

### Learning Objectives
- Optimize portfolio allocation using modern portfolio theory
- Balance risk and return using Sharpe ratio
- Account for real-world constraints

### Topics
- Markowitz mean-variance optimization
- Efficient frontier
- Sharpe ratio maximization
- Transaction costs and slippage
- Rebalancing strategies
- Risk management

### Lab
- Build portfolio optimizer
- Construct efficient frontier for asset universe
- Optimize portfolio with transaction cost constraints

---

## Final Project

**Duration**: 2-3 weeks

Students design and implement a complete trading system that:
1. Ingests and processes market data
2. Generates trading signals using ML models
3. Manages portfolio positions
4. Evaluates performance with appropriate metrics
5. Documents methodology and results

---

## Assessment

| Component | Weight |
|-----------|--------|
| Labs (8) | 40% |
| Final Project | 30% |
| Quizzes | 20% |
| Discussion Participation | 10% |
