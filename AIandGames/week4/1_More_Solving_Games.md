# Alpha Beta Pruning
[[1_adversarial_search]]

# Heuristics
* Often the game tree is too large to perform a minimax search to the terminal nodes at each evaluation function.
* Hence a `heuristic` can be used to evaluate the value of a non-terminal node.

## How to find a good Heuristic
* It needs to be normalized against the terminal values returned at actual terminal nodes.
* Trial and error can be used to compare heuristics against each other in multiple games to find which one is better.

## Combining Heuristics
![[Pasted image 20240122061331.png]]
* Sometimes multiple heuristics need to be used to prioritize multiple aspects of a game.
* They can be combined with a linear combination.
* The weights assigned to each heuristic can be either hand selected or using a stochastic hillclimber.
## Stochastic Hillclimber
* Perturb  the weights slightly using a random number generator.
* Compare the old and new values by playing them against each other. 
* Choose the best of the 2 and repeat.
* 