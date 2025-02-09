### USER DOCUMENTATION


1. Overview
This Connect 4 game is a Python application that uses Pygame to render a 7×6 grid and handle user interactions. One player (the human) plays against an AI (computer) with a Minimax-based strategy.

2. System Requirements
Python 3.7+
Pip (Python package manager)
NumPy (pip install numpy)
Pygame (pip install pygame)
3. Installation
Make sure you have Python installed (3.7 or newer).
Clone this repository either by the terminal or in github you can see "open with visual studio".


A new Pygame window will open, displaying the Connect 4 board.
5. Gameplay Instructions
Starting the Game

When the game begins, it randomly decides whether the Human (Player 1) or the AI (Player 2) goes first.
The text output in the console (and the color of the moving piece at the top) will reflect whose turn it is.
Human Player (Player 1)

Use your mouse to hover the circle at the top of the screen (in the grey rectangle).
Position the circle above the column where you want to drop your piece.
Click to drop your piece in that column.

After your turn, the AI will automatically calculate the best move and drop its piece.
You can see the AI’s piece in yellow.

!Winning Condition

The first player to place four of their pieces consecutively in a row, column, or diagonal wins.
If a player wins, a congratulatory message appears at the top of the screen.
Game Over

When a player achieves a winning line of four, or if the board is full (no valid moves left), the game ends.
After a short pause (3 seconds), the game window will close automatically.



### Developer Documentation
1. Introduction
This section provides an overview of the technical details of the Connect 4 application. It explains how the code is structured.


connect4.py: Contains all the logic for:
Creating and managing the board (using NumPy).
Rendering the game with Pygame.
Handling user input (mouse clicks).
The AI decision-making (Minimax with alpha-beta pruning).



4. Code Workflow
Initialization

The game starts by creating a 6×7 NumPy array (create_board) to represent the Connect 4 grid.
A Pygame window is created, and the board is drawn using draw_board.
The loop runs until game_over is True.

Event Handling:
If the user moves the mouse, a “preview” circle is drawn at the top to indicate where the piece might drop.
If the user clicks while it's Player 1’s turn, the code checks if the column is valid and drops a piece.

AI Move:
Uses the minimax function (with alpha-beta pruning) to determine the best column to drop a piece.
Once decided, it places the AI piece on the board.
Win Checking

After each turn, the game checks for a winning condition (winning_move).
If a player wins, a message is displayed, and game_over is set to True.

Game Over
When game_over is True, Pygame pauses for a moment, then closes automatically.


5. Function Overview & Docstrings

create_board()
Creates a 6×7 board filled with zeros (using NumPy).

drop_piece(board, row, col, piece)
Places a piece (Player or AI) into the board array at a specific row and column.

is_valid_location(board, col)
Checks if the topmost cell in a column is free (i.e., if a piece can be dropped there).

get_next_open_row(board, col)
Returns the index of the next available row in the specified column.

print_board(board)
Prints a flipped version of the board to the console (for debugging).

winning_move(board, piece)
Checks if the given piece (Player or AI) has connected four in a row anywhere.

evaluate_window(window, piece)
Scores a 1D array of four consecutive slots based on how favorable it is for a piece.

score_position(board, piece)
Evaluates the entire board, summing up evaluate_window results for horizontal, vertical, and diagonal segments.

get_valid_locations(board)
Returns a list of column indices where a piece can legally be dropped.

is_terminal_node(board)
Determines if the board is in a terminal state (someone won or the board is full).

minimax(board, depth, alpha, beta, maximizingPlayer)
Implements the Minimax algorithm with alpha-beta pruning to compute the best possible move for the AI.

depth: how many layers deep to search in the game tree.
alpha: the best score the maximizing player can guarantee so far.
beta: the best score the minimizing player can guarantee so far.
maximizingPlayer: True if we’re evaluating the AI’s best move, False if evaluating the player’s.

pick_best_move(board, piece)
A simpler, single-layer lookahead approach to pick a column (used for demonstration or alternative AI strategy).

draw_board(board)
Handles all the Pygame rendering, drawing the grid and pieces on the screen.

