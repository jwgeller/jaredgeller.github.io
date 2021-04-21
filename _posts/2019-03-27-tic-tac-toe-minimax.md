---
title: "Tic-Tac-Toe Minimax"
categories:
  - Davenport University
tags:
  - Artificial Intelligence
  - Class
---

# Problem Definition

Create a program where a human and a computer can play tic-tac-toe.  Use minimax evaluation of the tic-tac-toe game tree in the AI routine to choose the AI's next move.  

## Solution

Using information covering the concept of minimax evaluation in a game tree (Lucci & Kopec, 2016, pp. 112-114), I have developed a program where a human and a computer can play tic-tac-toe.

In this version of the game, the player (“X”) has their turn first. Then, using heuristic evaluation of the player’s position against open positions where the computer can play, the computer chooses a position which minimizes the potential for the player to win. The value which is minimized is calculated by determining:

- The number of threes-in-a-row that the player can complete
- The number of threes-in-a-row that the computer can complete

Every position is checked until the computer finds the first position which minimizes the difference between the two (computer count subtracted from player count). Note that the chosen position may not be the only position with the minimized difference due to game symmetry.

Two additional rules are programmed into the computer program’s decision-making routine:
- If the player can complete a three-in-a-row, the computer goes for a blocking move
- If the computer can complete a three-in-a-row, the computer goes for the win

Ideas for future improvements:
- Computer randomizes selection of symmetric moves (instead of simply selecting the first encountered)
- Computer has difficulty level options that provide the player with a chance to win

Here are direct links to GitHub and CodePen of the work:

[Tic-Tac-Toe Minimax GitHub](https://gist.github.com/jaredgeller/753cc2797a49f6819155911255d658f8)

[Tic-Tac-Toe Minimax CodePen](https://codepen.io/jaredgeller/pen/moQPwr)

-Jared

### References

Lucci, S. & Kopec, D. (2016). Artificial intelligence in the 21st century : a living introduction. Dulles, Virginia: Mercury Learning and Information.
