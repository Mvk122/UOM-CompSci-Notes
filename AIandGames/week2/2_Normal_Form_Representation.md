# Normal Form Representation
![[Pasted image 20231010171008.png]]
* Instead of using a tree, a table of strategies is used. (Tree-based representation is called extensive form).
* It is particularly suitable for simultaneous play games (i.e rock paper scissors).
	* All simultaneous play games are games of imperfect information because a decision is made not knowing what the other player is going to do.
* Can be easier to use for creating theories and for smaller games but is much more space inefficient than tree based representations.
	* This is because there needs to be a row and a column for every strategy pairing, even those that are impossible.

## Solved Games
* For any `2 player`, `zero sum` game with `perfect information` and `no chance`, one of the following is true:
	* Player 1 has a winning strategy.
	* Player 2 has a winning strategy.
	* Both players have strategies which at least ensure a draw.
* With these conditions, a game can be considered solved.

## Levels of Game Solutions
* `Weak`: Provides the strategy whereby one player can either win or draw starting at the beginning of the game.
* `Ultra Weak`: Proving which player can force a win or draw without providing the strategy.
* `Strong`: Providing a strategy that provides a win from any board state.