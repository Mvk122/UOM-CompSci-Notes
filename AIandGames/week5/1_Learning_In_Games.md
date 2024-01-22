# When to use Learning 
* When good heuristics cannot be found. 
* When there are too many branches in a decision tree. 
* When the equilibria are hard to compute due to:
	* Incomplete information. 
	* General sum games 
	* Games with many players

# Reinforcement Learning
* Learning where only the `quality` of the responses/ actions can be known, not what the `correct actions` are.
* The reinforcement information may only be available after a sequence of moves have been made.

# Exploration Exploitation Tradeoff
## Exploration 
* Find new states or new actions that may lead to higher rewards. 
## Exploitation 
* Perform actions that have worked well in the past.

# epsilon-greedy policy
* Balances the exploration exploitation tradeoff by using the best move with probability $