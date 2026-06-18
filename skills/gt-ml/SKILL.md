---
name: "gt-ml"
description: "Georgia Tech CS 7646 - Machine Learning for Trading. Use when learning ML applied to financial trading: technical analysis, classification algorithms, ensemble methods, reinforcement learning, and portfolio optimization."
metadata:
  university: "Georgia Tech"
  level: "intermediate"
  topics: ["machine learning", "trading", "classification", "ensemble methods", "reinforcement learning"]
  url: "https://www.udacity.com/course/machine-learning-for-trading--ud501"
---

# CS 7646 - Machine Learning for Trading

Georgia Tech course by Prof. Tucker Balch covering machine learning techniques applied to financial trading and portfolio management.

## Course Overview

This course bridges machine learning and quantitative finance. Students learn to build trading systems using ML algorithms, from simple nearest-neighbor classifiers to complex reinforcement learning agents and ensemble methods.

## Core Topics

### Module 1: Technical Analysis & Indicators
- **Bollinger Bands**: Upper/lower bands computed from rolling mean and standard deviation
- **RSI (Relative Strength Index)**: Momentum oscillator measuring speed and magnitude of price changes
- **MACD (Moving Average Convergence Divergence)**: Trend-following momentum indicator
- **Simple/Exponential Moving Averages**: Trend identification and signal generation

### Module 2: Data Structures & Manipulation
- NumPy arrays, Pandas DataFrames, and Series
- Date range indexing and rolling window operations
- Data normalization and resampling
- Handling missing data and outliers

### Module 3: ML Classification Algorithms
- **k-Nearest Neighbors (kNN)**: Instance-based learning for buy/sell signal classification
- **Decision Trees**: Recursive partitioning with information gain / Gini impurity
- **Random Forests**: Bagged decision trees with feature randomization
- **Bagging**: Bootstrap aggregating to reduce variance

### Module 4: Ensemble Methods
- Bagging vs. Boosting vs. Stacking
- Combining weak learners into strong predictors
- Out-of-bag error estimation
- Feature importance ranking

### Module 5: Support Vector Machines (SVMs)
- Maximum margin classifiers
- Kernel trick for non-linear boundaries
- Support Vector Regression (SVR) for price prediction
- Hyperparameter tuning (C, gamma, kernel selection)

### Module 6: Regression & Model Selection
- Linear regression for price/return forecasting
- Ridge and Lasso regularization
- Cross-validation and model evaluation metrics
- Avoiding overfitting: train/test splits, walk-forward validation

### Module 7: Reinforcement Learning
- Q-learning for optimal trade execution
- State-action-reward framework
- Epsilon-greedy exploration strategies
- Policy optimization for portfolio allocation

### Module 8: Portfolio Optimization & Strategy
- Mean-variance optimization (Markowitz)
- Sharpe ratio and risk-adjusted returns
- Efficient frontier construction
- Transaction cost modeling

## Key Formulas

```
# Bollinger Bands
Upper Band = SMA(20) + 2 * STD(20)
Lower Band = SMA(20) - 2 * STD(20)

# RSI
RS = Avg Gain(14) / Avg Loss(14)
RSI = 100 - (100 / (1 + RS))

# MACD
MACD Line = EMA(12) - EMA(26)
Signal Line = EMA(9) of MACD Line

# Sharpe Ratio
Sharpe = (Mean Return - Risk-Free Rate) / Std Dev Return
```

## Python Libraries Used

| Library | Purpose |
|---------|---------|
| `numpy` | Numerical computation, array operations |
| `pandas` | Data manipulation, time series analysis |
| `scikit-learn` | ML classifiers, regressors, ensemble methods |
| `matplotlib` | Visualization, charting |
| `QSTK` (QuantSoftware Toolkit) | Backtesting, market simulation |

## Practical Exercises

See `references/exercises.md` for hands-on projects and coding assignments.

## Reference Materials

- `references/syllabus.md` - Full course syllabus and module breakdown
- `references/key-concepts.md` - ML concepts with mathematical foundations
- `references/resources.md` - Additional reading, tools, and datasets

## Triggers

Activate this skill when the user:
- Asks about applying ML to stock trading or financial markets
- Needs help with technical indicators (Bollinger Bands, RSI, MACD)
- Wants to implement kNN, decision trees, random forests, or SVMs for trading
- Asks about reinforcement learning for trade execution
- Needs portfolio optimization or Sharpe ratio calculations
- References CS 7646, Georgia Tech ML for Trading, or Tucker Balch
