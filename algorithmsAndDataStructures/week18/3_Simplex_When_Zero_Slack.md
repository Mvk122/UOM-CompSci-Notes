# Simplex Algorithm When There is No Slack
* No slack in the augmented matrix can materialise when there is a slack variable with the value 0.
* This occurs when there exists 2 vertices, created through different constraints (eg a line passing straight through the origin) on the same point.
* This can cause an infinite loop as the simplex algorithm picking the option with the least slack as the `basic variable` can lead to it picking alternating points in a loop.
* This can be solved either by:
	* A loop detection algorithm. 
	* Using bland's rule.

## Bland's Rule
* If there is 0 slack and the all the possible `enterring variables` have a negative coefficient, then the `leaving variable` switches to the one with the smallest positive value.
* If some `entering variables` have a positive coefficient however, pick the one with the smallest positive coefficient.
* If multiple of the `leaving variables` have the same value, use a heuristic to choose one, generally based on their order in the table.