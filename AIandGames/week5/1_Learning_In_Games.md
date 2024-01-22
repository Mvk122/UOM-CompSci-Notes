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
* Balances the exploration exploitation tradeoff by using the best move with probability $e$ and a random move with probability $1-e$.
* Decrease $e$ with $O(1/t)$ to reward exploitation more as the game goes on.
* Should be used when the environment is not changing, a constant should be used instead if the environment is always changing.

# Tabular Reinforcement Learning Approach
![[Pasted image 20240122064607.png]]
* $r_t$ is the reward from doing a play.
* $a$ is a small positive learning rate (can use epsilon greedy policy).

# Q Function Approximation 
![[Pasted image 20240122065900.png]]
* In many real world scenarios, the state and action spaces are too large to judge the rewards for every given state and action explicitly. 
* Hence Q-Function approximation can be used to estimate the rewards for a given state and input.