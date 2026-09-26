# AI Checkers Engine & Move Evaluator

Building AI course project

## Summary

This project develops an intelligent AI engine for Checkers and board games, combining heuristic search with machine learning state evaluation to provide real-time optimal move predictions, blunder detection, and interactive game analysis.

## Background

Board games like Checkers are classic domains for exploring decision-making and artificial intelligence:
* Many amateur players make subtle positional errors without understanding why they lost.
* Full-depth minimax search can be computationally expensive on client-side web and mobile devices.
* My personal motivation is to bridge game theory and accessible machine learning by building interactive solvers that run seamlessly anywhere.

## How is it used?

The AI engine runs in the browser and mobile apps to provide instant game assistance:
* Players input or snap their current board position.
* The system evaluates candidate moves and ranks them by probability of winning.
* Explanations highlight tactical traps and suggest the highest-value sequence.

`python
def evaluate_move(board_state, weights):
    # Linear combination of positional features and piece advantages
    features = extract_features(board_state)
    score = sum(w * f for w, f in zip(weights, features))
    return score
`

## Data sources and AI methods

The project leverages self-play game datasets and standard endgame tablebases:
* Supervised classification for positional evaluation.
* Minimax with alpha-beta pruning for tactical decision lookahead.
* Evaluation weights tuned through simulated annealing and linear regression.

| Component | Technique |
| --- | --- |
| Move Search | Alpha-Beta Minimax |
| Positional Evaluation | Supervised Linear / NN Model |
| Optimization | Simulated Annealing |

## Challenges

What this project does not solve:
* It does not solve international 10x10 draughts (currently focused on standard 8x8 checkers).
* Real-time search depth is constrained by mobile hardware performance.

## What next?

Future expansions include:
* Deep reinforcement learning using Monte Carlo Tree Search (MCTS).
* Multi-variant board game support (Connect Four, Chess endgame).
* Automated natural-language blunder commentary.

## Acknowledgments

* Building AI course by University of Helsinki & Reaktor
* Python scientific computing ecosystem (NumPy, Scikit-learn)
