A game of Othello starts with white pieces on squares d4 and e5, and black pieces on squares d5 and e4. The remaining squares are empty.

Two players, called Black and White, from the color of the pieces they use, take part in the game. The Black player starts the game.

Players take turns making one move consisting of placing a piece of their color on the board. If all the squares in a line—meaning in a row, column, or diagonal—between the piece just placed and another piece of the same color are pieces of the opposite color, they change color, meaning they are flipped. Placing one piece on the board can cause several lines of pieces to change at the same time.

A move is legal only if it results in changing the color of at least one piece on the board. If at any moment a player cannot make a legal move, they pass and do not place a piece on the board.

Although it is not strictly in accordance with the rules of Othello, in this program we allow a player to pass even if they can make a legal move.

Another rule, which also does not apply here, states that the game automatically ends when neither player can make a legal move. The winner is then the player with more pieces of their color on the board.


The goal is to write a program that allows two players to play a game of Othello, without counting scores and determining the winner.

***

The program, in a loop:

writes a prompt indicating whose turn it is and what legal moves they can make;
reads the current player's command;
if it reads a command to interrupt the game, it ends its work;
if it reads a command to pass on a move, it returns to the start of the loop;
if it reads a command to make a move, it makes that move and returns to the start of the loop.
The program does not finish working before reaching the command to interrupt the game, even if it determines that neither player can make a legal move. It also does not recognize as an error situations where a user passes on a move or asks to interrupt the game, even though they can make a legal move.
It is assumed that the input is correct.
