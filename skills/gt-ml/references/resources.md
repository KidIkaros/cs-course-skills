# CS 7646 - Additional Resources

## Course Materials

### Official
- **Udacity Course**: https://www.udacity.com/course/machine-learning-for-trading--ud501
- **Georgia Tech OMS CS**: https://oms.gatech.edu/
- **Prof. Tucker Balch**: https://www.cc.gatech.edu/~balch/

### Lecture Notes & Slides
- Course slides available on Udacity platform
- Supplementary notes in CS 7646 GitHub repositories

---

## Python Libraries & Tools

### Core Data Science Stack
| Library | Installation | Documentation |
|---------|--------------|---------------|
| NumPy | `pip install numpy` | https://numpy.org/doc/ |
| Pandas | `pip install pandas` | https://pandas.pydata.org/docs/ |
| Matplotlib | `pip install matplotlib` | https://matplotlib.org/ |
| SciPy | `pip install scipy` | https://docs.scipy.org/ |

### Machine Learning
| Library | Installation | Documentation |
|---------|--------------|---------------|
| scikit-learn | `pip install scikit-learn` | https://scikit-learn.org/stable/ |
| XGBoost | `pip install xgboost` | https://xgboost.readthedocs.io/ |
| LightGBM | `pip install lightgbm` | https://lightgbm.readthedocs.io/ |

### Financial Data
| Library | Installation | Documentation |
|---------|--------------|---------------|
| yfinance | `pip install yfinance` | https://pypi.org/project/yfinance/ |
| Alpha Vantage | `pip install alpha-vantage` | https://www.alphavantage.co/documentation/ |
| Quandl (Nasdaq Data Link) | `pip install quandl` | https://docs.data.nasdaq.com/ |
| pandas-datareader | `pip install pandas-datareader` | https://pandas-datareader.readthedocs.io/ |

### Backtesting
| Library | Installation | Documentation |
|---------|--------------|---------------|
| backtrader | `pip install backtrader` | https://www.backtrader.com/ |
| Zipline | `pip install zipline-reloaded` | https://zipline.io/ |
| QuantConnect | Cloud platform | https://www.quantconnect.com/ |

### Visualization
| Library | Installation | Documentation |
|---------|--------------|---------------|
| Plotly | `pip install plotly` | https://plotly.com/python/ |
| Seaborn | `pip install seaborn` | https://seaborn.pydata.org/ |
| mplfinance | `pip install mplfinance` | https://github.com/matplotlib/mplfinance |

---

## Recommended Reading

### Books

#### Machine Learning
1. **"Hands-On Machine Learning with Scikit-Learn, Keras, and TensorFlow"** - Aurelien Géron
   - Comprehensive ML guide with practical examples
   - Chapters on ensemble methods, decision trees, SVMs

2. **"An Introduction to Statistical Learning (ISLR)"** - James, Witten, Hastie, Tibshirani
   - Free PDF available: https://www.statlearning.com/
   - Excellent statistical foundations

3. **"The Elements of Statistical Learning"** - Hastie, Tibshirani, Friedman
   - More advanced treatment: https://hastie.su.domains/ElemStatLearn/

4. **"Pattern Recognition and Machine Learning"** - Christopher Bishop
   - Bayesian perspective on ML

#### Quantitative Finance
1. **"Quantitative Trading"** - Ernest Chan
   - Practical guide to building trading systems
   - Covers backtesting, risk management, strategies

2. **"Algorithmic Trading"** - Ernest Chan
   - Advanced topics in automated trading

3. **"Advances in Financial Machine Learning"** - Marcos López de Prado
   - Cutting-edge ML applications in finance
   - https://www.wiley.com/en-us/Advances+in+Financial+Machine+Learning-p-9781119482086

4. **"Machine Learning for Asset Managers"** - Marcos López de Prado
   - Concise, practical guide

5. **"Quantitative Risk Management"** - McNeil, Frey, Embrechts
   - Risk modeling foundations

6. **"Expected Returns"** - Antti Ilmanen
   - Comprehensive overview of return premia

#### Python for Finance
1. **"Python for Finance"** - Yves Hilpisch
   - Python-centric financial analysis

2. **"Python for Data Analysis"** - Wes McKinney
   - Pandas creator's guide

---

### Online Resources

#### Financial Data Sources
- **Yahoo Finance** (via yfinance): Free historical data
- **Quandl/Nasdaq Data Link**: Free and premium datasets
- **Alpha Vantage**: Free API for stocks, forex, crypto
- **SEC EDGAR**: Company filings and financial reports
- **FRED**: Federal Reserve Economic Data

#### Tutorials & Guides
- **Quantitative Economics with Python**: https://python.quantecon.org/
- **PyQuant News**: https://pyquantnews.com/
- **QuantStart**: https://www.quantstart.com/
- **Alpaca Docs**: https://alpaca.markets/docs/

#### GitHub Repositories
- **CS 7646 Course Materials**: Search "CS 7646" on GitHub
- **QuantSoftware Toolkit**: https://github.com/quantopian/qstk
- **Zipline**: https://github.com/quantopian/zipline
- **Backtrader Examples**: https://github.com/mementum/backtrader/tree/master/samples

---

## Research Papers

### Foundational
- Markowitz, H. (1952). "Portfolio Selection." *Journal of Finance*
- Fama, E. (1970). "Efficient Capital Markets: A Review of Theory and Empirical Work"
- Breiman, L. (2001). "Random Forests." *Machine Learning*

### ML in Finance
- Gu, S., Kelly, B., & Xiu, D. (2020). "Empirical Asset Pricing via Machine Learning." *Review of Financial Studies*
- Dixon, M., Halperin, I., & Bilokon, P. (2020). *Machine Learning in Finance*
- Sirignano, J. & Cont, R. (2019). "Universal Features of Price Formation in Financial Markets." *PNAS*

### Reinforcement Learning for Trading
- Moody, J. & Saffell, M. (2001). "Learning to Trade via Direct Reinforcement." *IEEE Trans. Neural Networks*
- Deng, Y., Bao, F., Kong, Y., Ren, Z., & Dai, Q. (2017). "Deep Direct Reinforcement Learning for Financial Signal Representation and Trading." *IEEE Trans. Neural Networks*

---

## Datasets for Practice

### Historical Stock Data
```
# Using yfinance
import yfinance as yf

# Single stock
data = yf.download('AAPL', start='2010-01-01', end='2024-01-01')

# Multiple stocks
tickers = ['AAPL', 'MSFT', 'GOOGL', 'AMZN']
data = yf.download(tickers, start='2010-01-01', end='2024-01-01')
```

### Alternative Data Sources
- **Quandl WIKI**: Historical stock data (free, legacy)
- **SEC EDGAR**: 10-K, 10-Q filings
- **Earnings transcripts**: Sentiment analysis opportunities
- **Options chains**: Options pricing data

---

## Online Courses & MOOCs

### Complementary Courses
1. **Stanford CS229**: Machine Learning (Andrew Ng)
2. **MIT 18.S096**: Topics in Mathematics with Applications in Finance
3. **CMU 18-447**: Introduction to Deep Learning for Natural Language Processing
4. **Coursera Financial Engineering**: Columbia University specialization

### MOOCs
- **Coursera**: "Machine Learning and Reinforcement Learning in Finance" (NYU)
- **edX**: "Machine Learning for Finance" (NYU)
- **DataCamp**: Financial analysis tracks

---

## Tools & Platforms

### Paper Trading
- **Alpaca**: Commission-free API trading
- **Interactive Brokers**: Professional platform with API
- **TD Ameritrade**: Paper trading account
- **TradingSim**: Simulated trading platform

### Backtesting Platforms
- **QuantConnect**: Cloud-based, free tier available
- **Quantopian** (archived): Historical lectures still valuable
- **Backtrader**: Python framework, local
- **Zipline**: Python framework, local

### Data Visualization
- **TradingView**: Advanced charting platform
- **Plotly Dash**: Build interactive dashboards
- **Streamlit**: Rapid prototyping for data apps

---

## Community & Forums

### Discussion Forums
- **r/algotrading**: Reddit algorithmic trading community
- **r/QuantFinance**: Quantitative finance discussions
- **QuantStack Exchange**: https://quant.stackexchange.com/
- **Stack Overflow**: [python] + [finance] + [machine-learning] tags

### Newsletters
- **Quantocracy**: Curated quant news
- **QuantStart Newsletter**: Trading and investing insights
- **Python for Finance**: Newsletter by Yves Hilpisch

### Conferences
- **QuantMinds**: Leading quant finance conference
- **Machine Learning in Finance**: Various venues
- **NeurIPS/ICML workshops**: Financial ML tracks

---

## Career Resources

### Quantitative Finance Roles
- Quantitative Analyst/Researcher
- Quantitative Developer
- Algorithmic Trader
- Data Scientist (Finance)
- Risk Analyst

### Skills to Develop
- Python (pandas, NumPy, scikit-learn)
- SQL and database management
- Statistics and probability
- Financial markets knowledge
- Communication and visualization

### Job Boards
- **eFinancialCareers**: https://efinancialcareers.com/
- **QuantNet**: https://quantnet.com/
- **H1B Salary Database**: Check quant roles
- **LinkedIn**: #quantfinance, #algotrading

---

## Quick Reference: Common Imports

```python
# Data manipulation
import numpy as np
import pandas as pd
from datetime import datetime

# Visualization
import matplotlib.pyplot as plt
import seaborn as sns

# Machine learning
from sklearn.model_selection import train_test_split
from sklearn.metrics import accuracy_score, classification_report
from sklearn.preprocessing import StandardScaler
from sklearn.ensemble import RandomForestClassifier, AdaBoostClassifier
from sklearn.tree import DecisionTreeClassifier
from sklearn.svm import SVC
from sklearn.neighbors import KNeighborsClassifier
from sklearn.linear_model import LinearRegression, Ridge, Lasso

# Financial data
import yfinance as yf

# Backtesting (example)
import backtrader as bt
```
