# Theory Of Games

## Definitions
* `Best Response`: For a given player and all opponent strategies fixed, the best response is the strategy for the player that gives the best payoff.
* `Nash Equilibrium`: A strategy profile (strategy for every player in the game) if each strategy in the profile is a best response to all of the others.
	* If players are playing the Nash, no player has any incentive to change its strategy unilaterally as there would be no strategy that has a higher payoff with a change of strategy.
	* Every game with a finite number of players where each player has a finite number of pure strategies has at least one nash equilibrium (including when using mixed strategies).
## Best Response
* It is always possible to find a best response if there is a finite strategy space.
* If the strategy space is infinite then it may not always be possible.

# Finding Nash Equilibriums
![[Pasted image 20240122033856.png]]
* Consider 2 players, a maximizing player (Amelia) and a minimizing player (Scott)
* For each strategy that Amelia can play, get the minimum value for them and out of those strategies, choose the row with the max of these minimums.
* For each strategy that Scott can play, get the maximum that he can get and choose the column with the minimum of these maximums.
* Any intersections where the max of the min and the min of the max are the same (in this case `3`) are the strategies with the `nash equilibrium`.

# Dominating Strategy
* A strategy $s_i$  dominates $s_j$ if for all strategies by other players, it has a better payoff than $s_j$ in each given strategy pair.
* Strategies which are dominated can be removed as in all cases, their dominating strategy is a better move.

# Mixed Strategies
![[Pasted image 20240122035350.png]]
* A strategy for which a player probabilistically plays a combination of pure strategies and receives a probabilistic combination of payoffs.
* May be required when there is hidden information.