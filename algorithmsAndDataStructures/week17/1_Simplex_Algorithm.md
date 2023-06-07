# Simplex Algorithm
#SimplexAlgorithm #linearProgramming 
* Since the solution exists on one of the intersections of the constraints, the simplex method is an algorithm to iterate through the intersections that exist within the constraint graph (are feasible) until a maximal solution is found.
## Simplex Algorithm Requirements
* The feasible region, when graphed must have a convex shape. (All the angles are less than 180 degrees).
* The origin should be in the feasible region.

## Slack Variables
* Slack variables are variables that convert equations of the form $ax <= b$ to $ax + s_1 = b$, thereby eliminating the "slack" in the equation.
* The coefficient of the slack variables is always 1 and each slack variable only exists in one equation, for example to convert these set of constraints:
$-x_1 + x_2 \le 11$
$x_1 + x_2 \le 27$
$2x_1 +5x_2 \le 50$
We get:
$-x_1 + x_2 + s_1 = 11$
$x_1 +x_2 + s_2 = 27$
$2x_1 + 5x_2 + s_3 = 50$
* The variables that exist in only one equation are `basic variables` and the ones that exist in multiple are called `non-basic variables`.
* A `basic` solution can be derived by setting the `non-basic` variables to 0.

## Running the Simplex Algorithm
* The simplex algorithm works on the principle that by swapping variables around, we can iterate through the intersections until the best possible solution is formed.
* We want to maximize `z` where `z - maximising_equation = 0`.
* The steps are as follows:
	1. Create the solution matrices where each equation contains all of the slack variables, setting their coefficients to 0 in equations where the slack variable isn't originally from:![[Pasted image 20230426145054.png]]
	2.  Represent it as an augmented matrix:![[Pasted image 20230426145123.png]]
	3. The `non-basic variable` to be chosen is the variable with the largest negative coefficient in the maximizing vector, in this case $x_2$ with coefficient $-6$. This is now known as the `enterring variable` as it is entering the set of basic variables.
	4. The `basic variable` to be chosen is the variable that introduces the least slack when dividing it by the coefficient of the basic variable. In this case, it is $s_1$ as it has the slack of 11. (Using the coefficient of $x_2$ being 1). This is now known as the `leaving variable.` (The least non-negative value is chosen).
	5. gaussian elimination now needs to be done on each of the rows where:
		* The column of the `enterring variable` must become 0 through gaussian elimination except for the row with the `leaving variable`.
		* The intersection of the row of the `leaving variable` and the column of the `enterring variable` must be set to 1.
	6. Gaussian elimination can be done by multiplying either the row in question or the row of the `leaving variable` and adding them together to satisfy the constraints above.
	7. This gives the following solution where:
		* The value of the solution is 66.
		* The current solution being considered is $x_1 = 0 x_2 = 11$.![[Pasted image 20230426151517.png]]
	8. Repeat the above using the augmented matrix as shown until there are no more negative numbers in the bottom row (the row with 10 0 6 0 etc).
		* This is because negative coefficients mean that there is more room for z to become larger in the equation `z - maximising_equation = 0`.