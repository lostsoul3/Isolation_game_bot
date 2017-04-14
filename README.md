# Isolation_game_bot


# Build a Game-playing Agent

## Synopsis

Isolation is a deterministic, two-player game of perfect information in which the players alternate turns moving a single piece from one cell to another on a board.  Whenever either player occupies a cell, that cell becomes blocked for the remainder of the game.  The first player with no remaining legal moves loses, and the opponent is declared the winner.

Here, we will play a version of Isolation where each agent is restricted to L-shaped movements (like a knight in chess) on a rectangular grid (like a chess or checkerboard).  The agents can move to any open cell on the board that is 2-rows and 1-column or 2-columns and 1-row away from their current position on the board. (Movements are blocked at the edges of the board -- there is no wrap around.)

Additionally, agents will have a fixed time limit each turn to search for the best move and respond.  If the time limit expires during a player's turn, that player forfeits the match, and the opponent wins.

These rules are implemented in `isolation.Board` class provided in the repository. The `Board` class exposes an API including `is_winner()`, `is_loser()`, `get_legal_moves()`, and other methods available for your agent to use.

You may write or modify code within each file (as long as you maintain compatibility with the function signatures provided) and you may add other classes, functions, etc., as you need.


## Implementation

### Adversarial Search

Implemented the minimax algorithm, then implemented alpha-beta pruning for minimax, and finally incorporated iterative deepening.The class constructor takes arguments that specify whether to call minimax or alphabeta search, and whether to use fixed-depth search or iterative deepening. 

The required interface specifications can be found in the docstrings for each function.

### Evaluation Functions

Three heuristic functions have been developed to inform the value judgements your AI will make when choosing moves.These are compared in the report heuristic_analysis.pdf.

`tournament.py` is used to evaluate and compare heuristic functions by testing the agent & heuristic against agent configuations that we specify in the tournament script.  The script plays your agent against each one of the test agents - which have all been ranked with a calibrated Elo score (a skill rating system used in many games) - to determine the relative strength of your heuristic and search algorithm.  You will need the score returned by this script for each of your evaluation functions to include in your report.


## Testing

### Test Players

We have also provided `sample_players.py` containing 3 player classes for you to test against locally:

- `RandomPlayer` - randomly selects a move from among the available legal moves
- `GreedyPlayer` - selects the next legal move with the highest heuristic value
- `HumanPlayer`  - allows *YOU* to play against the AI through the terminal


### Unit Tests

The `agent_test.py` script contains unittest test cases to evaluateimplementations.  The test cases evaluate your functions compared to a static set of example game trees to verify that the correct output is returned, and that each algorithm visits an expected number of nodes during search.

### Tournament

The `tournament.py` script will run a round-robin tournament between your CustomPlayer agent with itertive deepening and your custom heuristic function against several calibrated agent configurations using fixed-depth minimax and alpha-beta search with the example heuristics provided in `sample_players.py`.
