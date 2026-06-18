# CS 229 — Resources

## Official Course Materials

| Resource | URL |
|----------|-----|
| Course Homepage | https://cs229.stanford.edu/ |
| Main Course Notes (PDF) | https://cs229.stanford.edu/main_notes.pdf |
| Past Problem Sets | https://cs229.stanford.edu/ |
| Past Exams | https://cs229.stanford.edu/ |

## Video Lectures

| Resource | URL |
|----------|-----|
| Andrew Ng's CS 229 (YouTube) | https://www.youtube.com/playlist?list=PLoROMvodv4rMiGQp3WXShtMGgzqpfVfbU |
| Stanford Online (full course) | https://online.stanford.edu/courses |

## Textbooks

| Book | Author(s) | Notes |
|------|-----------|-------|
| *Pattern Recognition and Machine Learning* | Christopher Bishop | Primary reference for probabilistic ML, EM, graphical models |
| *The Elements of Statistical Learning* | Hastie, Tibshirani, Friedman | Comprehensive ML theory, freely available at https://hastie.su.domains/ElemStatLearn/ |
| *Introduction to Probability* | Bertsekas & Tsitsiklis | Used at MIT, excellent for prerequisites |
| *Convex Optimization* | Boyd & Vandenberghe | For SVM duality, optimization. Freely available at https://web.stanford.edu/~boyd/cvxbook/ |
| *Deep Learning* | Goodfellow, Bengio, Courville | For extensions into deep learning |
| *Reinforcement Learning: An Introduction* | Sutton & Barto | Standard RL reference. Freely available at http://incompleteideas.net/book/the-book.html |

## Python Libraries

| Library | Use Case |
|---------|----------|
| `numpy` | Linear algebra, core computations |
| `scipy` | Optimization, distributions, sparse matrices |
| `scikit-learn` | Implementations of most algorithms in this course |
| `cvxpy` | Convex optimization (SVMs, regularized problems) |
| `matplotlib` | Visualization |
| `pandas` | Data loading and manipulation |
| `jupyter` | Interactive notebooks for experimentation |

## Key Scikit-Learn Classes

```python
from sklearn.linear_model import LinearRegression, LogisticRegression
from sklearn.svm import SVC, SVR
from sklearn.cluster import KMeans
from sklearn.mixture import GaussianMixture
from sklearn.decomposition import PCA
from sklearn.naive_bayes import GaussianNB
from sklearn.model_selection import cross_val_score
from sklearn.preprocessing import StandardScaler
```

## Problem Set Sources

| Source | URL |
|--------|-----|
| CS 229 Past Problem Sets | https://cs229.stanford.edu/ |
| MIT 6.034 (AI) Problem Sets | https://ocw.mit.edu/courses/6-034-artificial-intelligence-fall-2010/ |
| Coursera ML (Andrew Ng) | https://www.coursera.org/learn/machine-learning |
| Bishop's PRML Exercises | Appendix A of *Pattern Recognition and Machine Learning* |

## Online Tools

| Tool | URL | Purpose |
|------|-----|---------|
| Desmos | https://www.desmos.com/ | Visualize functions, gradients |
| Overleaf | https://www.overleaf.com/ | LaTeX for problem set writeups |
| Google Colab | https://colab.research.google.com/ | Free GPU for coding assignments |
| Kaggle | https://www.kaggle.com/ | Datasets and competitions |

## Supplementary Lectures & Notes

| Resource | URL |
|----------|-----|
| CS 229 Discussion Notes | https://cs229.stanford.edu/ |
| Math for ML (book) | https://mml-book.github.io/ |
| Distill.pub (ML explanations) | https://distill.pub/ |
| Lilian Weng's Blog | https://lilianweng.github.io/ |
| Sebastian Raschka's Blog | https://sebastianraschka.com/ |

## Related Stanford Courses

| Course | Topic | URL |
|--------|-------|-----|
| CS 221 | Artificial Intelligence | https://cs221.stanford.edu/ |
| CS 224N | NLP with Deep Learning | https://web.stanford.edu/class/cs224n/ |
| CS 231N | CNNs for Visual Recognition | https://cs231n.stanford.edu/ |
| CS 224W | Machine Learning with Graphs | https://web.stanford.edu/class/cs224w/ |
| STATS 110 | Probability | https://stat110.net/ |
| STATS 315A | Statistical Learning | https://web.stanford.edu/class/stats315a/ |
