#SimplexAlgorithm 
# Simplex Algorithm when the origin is not a feasible solution
* The simplex algorithm requires that the first solution considered (usually the origin) is a feasible solution. 
* This can be mitigated by adding artificial variables that allow the origin to be a valid solution, then penalising the use of the artificial variable in the "maximise" vector so that the value of the artificial variable will be 0 in the optimal solution.

## Adding Artificial Variables
![[Pasted image 20230426155107.png]]
* For the above constraints, the artificial variable can be added to the second equation. The artificial variable must also be added to the "maximise" vector to ensure that it is not present in the final solution: 
![[Pasted image 20230426155212.png]]
* This can be converted into the vector form as follows:\
![[Pasted image 20230426155251.png]]
* The `enterring variable` will then be $a_1$ to remove it from the solution and the `leaving variable` will be $s_2$ as it is negative and contributes to the solution being infeasible.
* This results in the following augmented matrix, the simplex method can then be run as normal: ![[Pasted image 20230426155613.png]]