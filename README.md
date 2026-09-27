# AI Checkers Engine & Move Evaluator 🏁

[![Building AI - Honors](https://img.shields.io/badge/Building_AI-Advanced_Track_(Honors)-success?style=flat-square&logo=academia)](https://github.com/Machine4321/building-ai-project)
[![Python](https://img.shields.io/badge/Python-3.10+-blue?style=flat-square&logo=python)](https://python.org)
[![Live Platform](https://img.shields.io/badge/Live_Web_App-nextcheckersmove.com-orange?style=flat-square&logo=google-chrome)](https://nextcheckersmove.com)
[![Google Play](https://img.shields.io/badge/Google_Play-Android_App-green?style=flat-square&logo=google-play)](https://nextcheckersmove.com)

**Capstone Project for University of Helsinki & MinnaLearn — Building AI (Advanced Track with Honors)**  
*Author:* **Mikko Palovuori** ([github.com/Machine4321](https://github.com/Machine4321))

---

## 📌 Summary

This project develops an intelligent AI engine for board games and Checkers, combining heuristic search with machine learning state evaluation to provide **real-time optimal move predictions, blunder detection, and interactive game analysis**. 

The architecture conceptualized and prototyped in this project serves as the computational foundation for the production web platform and Android application deployed at **[nextcheckersmove.com](https://nextcheckersmove.com)**.

---

## 🎯 Background & Motivation

Board games like Checkers are classic testbeds for decision-making, game theory, and search tree optimization:
* **Tactical Complexity:** Many amateur and club players make subtle positional errors without understanding the long-term strategic penalty.
* **Client-Side Latency:** Exhaustive minimax search trees quickly explode in complexity ($O(b^d)$); running high-depth analysis on client-side web browsers or mobile devices requires efficient pruning and optimized state evaluation.
* **Goal:** Bridge classical heuristic game theory with modern machine learning to build an accessible, instantaneous move evaluator and blunder detector.

---

## ⚙️ Architecture & AI Methods

The engine combines tree-search lookahead with trained positional weights:

```
[ Board State Input ]
         │
         ▼
[ Legal Moves Generator ] ──► [ Transposition Table / Cache ]
         │
         ▼
[ Minimax Search (Alpha-Beta Pruning) ]
         │
         ▼
[ Positional State Evaluator ] ◄── [ Feature Weights (Tuned via Simulated Annealing) ]
         │
         ▼
[ Ranked Moves & Blunder Analysis ]
```

### Key AI Components:

| Component | AI & Algorithmic Technique | Purpose |
| :--- | :--- | :--- |
| **Move Search Engine** | **Minimax with Alpha-Beta Pruning** | Explores candidate moves while pruning provably suboptimal branches. |
| **Heuristic Evaluation** | **Linear Weight Model / Positional Scoring** | Scores piece advantages, king safety, center control, and runaway pawns. |
| **Weight Optimization** | **Simulated Annealing & Regression** | Optimizes heuristic coefficient vectors against historical match databases. |
| **Game Search Cache** | **Zobrist Hashing / Transposition Tables** | Eliminates redundant calculations across recurring game states. |

### Evaluation Heuristic Example:

```python
def evaluate_board_state(board, weights):
    """
    Computes a linear evaluation score for a given board position.
    Positive values favor Player 1; negative values favor Player 2.
    """
    features = extract_positional_features(board)
    # Features include: piece count, kings, center control, mobility, back-rank protection
    return sum(w * f for w, f in zip(weights, features))
```

---

## 📱 Real-World Deployment

This project was actively extended from an academic design into a production commercial application:
* 🌐 **Web Platform:** [nextcheckersmove.com](https://nextcheckersmove.com)
* 📲 **Android App:** Published on the Google Play Store for instant mobile board analysis.

---

## 🚀 Future Roadmap

* Deep reinforcement learning using Monte Carlo Tree Search (MCTS) inspired by AlphaZero.
* Automated natural-language blunder commentary using large language model (LLM) APIs.
* Expansion into related state-space games (Connect Four, Reversi / Othello).

---

## 📜 Acknowledgments & License

* Developed as part of the **Building AI** course by the **University of Helsinki** & **MinnaLearn**.
* Built with Python, NumPy, and Scikit-learn.
