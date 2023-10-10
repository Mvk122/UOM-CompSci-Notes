# Game Theory

## Definitions
* `Game`: A scenario with a finite number of players, and a finite tree where each node of the tree is associated with a possible move that a player can move from that current position.
* `Zero Sum Game`: A game with the property that the sum of payoffs for all players is 0 at each leaf node.
## Game Trees
* Explained in [[1_adversarial_search]]
## Chance in Game Trees
![[Pasted image 20231010154311.png]]
* Chance can be represented in game trees by adding an additional player, `chance`.
* Each action by `chance` has an associated probability and the `chance` player gets no payoff.
## Imperfect Information in Game Trees
* In some games, players may not always know what other players know.
* Hence in an `imperfect information game`, the player does not always know where it is in the game tree.
* Thus an `information set` needs to be created for each player which is a set of nodes a player could be at given the information it has.
* In each of these nodes, the action taken must be the `same` for all nodes in the information set.
* For a game with imperfect information, you cannot always find a winning strategy.

