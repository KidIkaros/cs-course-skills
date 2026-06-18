# CS 221 Resources

## Primary Resources

### Course Materials
- **Course website**: [stanford-cs221.github.io/spring2026](https://stanford-cs221.github.io/spring2026/)
- **Lecture notes**: available on course site (PDF/HTML)
- **Video lectures**: posted after each lecture on course website
- **Sections**: weekly TA-led review sessions with problem-solving

### Textbook
- **Artificial Intelligence: A Modern Approach** (4th Edition)
  - Authors: Stuart Russell & Peter Norvig
  - Publisher: Pearson
  - ISBN: 978-0134610993
  - Companion site: [aima.cs.berkeley.edu](http://aima.cs.berkeley.edu/)
  - Every module maps to specific chapters

---

## Supplementary Textbooks

| Title | Authors | Focus |
|-------|---------|-------|
| *Pattern Recognition and Machine Learning* | Bishop | Probabilistic ML (Ch. 8–12 useful) |
| *Deep Learning* | Goodfellow et al. | Neural networks theory |
| *Reinforcement Learning: An Introduction* | Sutton & Barto | RL deep dive |
| *Artificial Intelligence: Foundations of Computational Agents* | Poole & Mackworth | Alternative intro text |
| *Probabilistic Robotics* | Thrun, Burgard, Fox | Robotics + SLAM |

---

## Online Courses & Lectures

- **Stanford CS 221 (YouTube)**: full lecture recordings from previous offerings
- **Berkeley CS 188**: similar course with excellent video lectures
- **MIT 6.034**: Patrick Winston's classic AI lectures (archived)
- **DeepMind x UCL RL Course**: David Silver's reinforcement learning series
- **Fast.ai**: practical deep learning (good complement to theory)

---

## Tools & Libraries

### Python AI/ML Stack
- **NumPy**: array operations, linear algebra
- **Pandas**: data manipulation and analysis
- **Scikit-learn**: ML algorithms, model evaluation
- **PyTorch**: neural networks, automatic differentiation
- **TensorFlow / Keras**: alternative deep learning framework
- **OpenAI Gym (Gymnasium)**: RL environments and benchmarks

### Search & CSP
- **AIMA Python**: [github.com/aimacode/aima-python](https://github.com/aimacode/aima-python) — implementations of all textbook algorithms
- **python-constraint**: library for constraint satisfaction problems
- **OR-Tools**: Google's optimization library (CSP, routing, scheduling)

### Visualization
- **Matplotlib**: plotting and charts
- **Graphviz**: graph/network visualization
- **D3.js**: interactive visualizations
- **Netron**: neural network architecture visualization

---

## Practice Problems & Competitions

### Coding Challenges
- **LeetCode**: search, graph algorithms, DP problems
- **Codeforces**: competitive programming (algorithms focus)
- **Advent of Code**: annual puzzle competition

### AI Competitions
- **Kaggle**: ML competitions across domains
- **AIcrowd**: RL and multi-agent competitions
- **RoboCup**: robotics competition (advanced)

### Problem Set Archives
- **Stanford CS 221 past exams**: available on course website
- **Berkeley CS 188 past exams**: similar format and difficulty
- **AIMA online exercises**: chapter-by-chapter practice

---

## Papers & Advanced Reading

### Foundational Papers
- Russell & Norvig (various): rational agent framework
- Dijkstra (1959): shortest path algorithm
- Hart, Nilsson, Raphael (1968): A* algorithm
- Bellman (1957): dynamic programming and MDPs
- Rumelhart, Hinton, Williams (1986): backpropagation
- LeCun et al. (1998): gradient-based learning applied to document recognition

### Modern AI
- Vaswani et al. (2017): Attention Is All You Need (transformers)
- Silver et al. (2016): Mastering Go with deep neural networks and tree search
- Mnih et al. (2015): Human-level control through deep RL
- Goodfellow et al. (2014): Generative adversarial networks

---

## Community & Support

- **Piazza**: course Q&A forum (check course website for current offering)
- **Office hours**: instructor and TA office hours (schedule on course site)
- **Study groups**: Piazza study groups or section-matching
- **Stanford AI community**: Stanford AI Lab (SAIL), Stanford HAI

---

## Reference Guides

### Algorithm Complexity Cheat Sheet
```
Search:       BFS O(b^d)  |  DFS O(b^m)  |  A* O(b^d) with good h
Minimax:      O(b^m)      |  α-β O(b^{m/2})
CSP:          BT O(d^n)   |  AC-3 O(cd³)  |  Min-conflicts O(n·d·k)
MDP:          VI O(|S|²|A|)  |  PI O(|S|³) per iter
ML:           SGD O(n·d·iter)  |  Backprop O(n·w·iter)
```

### Common Pitfalls
1. **Confusing admissibility with consistency** — consistency implies admissibility, not vice versa
2. **Forgetting discount factor in MDPs** — undiscouted MDPs may not converge
3. **Overfitting in ML** — always use held-out test data
4. **Ignoring computational complexity** — polynomial in theory, exponential in practice
5. **Confusing precision with recall** — understand your use case before optimizing

### Formula Reference
```
# Search
f(n) = g(n) + h(n)          # A* evaluation

# MDP
V*(s) = max_a Σ_s' T(s,a,s')[R(s,a,s') + γV*(s')]   # Bellman optimality
V_{k+1}(s) = max_a Σ_s' T(s,a,s')[R(s,a,s') + γV_k(s')]  # Value iteration update

# Machine Learning
L(w) = (1/n) Σ L(f_w(x_i), y_i) + λ||w||²   # Regularized loss
w ← w - α ∇L(w)                              # Gradient descent update

# Bayes
P(A|B) = P(B|A)P(A) / P(B)                   # Bayes' rule
```
