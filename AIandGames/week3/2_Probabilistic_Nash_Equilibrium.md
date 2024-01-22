# Probabilistic Nash Equilibrium
* To find the nash equilibrium, find the expected payoff against each of the strategies of the opponent and find the strategy x which makes them equal. 
* We want it to be equal so either player has no reason to unilaterally change their strategy.

# Probabilistic Nash Example
![[Pasted image 20240122043125.png]]
* Eric wins 1 if they are in the same room and Donald wins 1 if they are not.
* Let x be the probability that Donald goes to blue
* If eric always goes to red, his expected value is:
$$
(-1)x + (1)(1-x) = 1 -2x
$$
* If eric always goes to blue his expected value is:
$$
(-1)(1-x) + (1)(x) = 2x - 1
$$
* Then the value donald should choose for x is: 
$$
1 - 2x = 2x - 1
$$
$$
x = 0.5
$$
