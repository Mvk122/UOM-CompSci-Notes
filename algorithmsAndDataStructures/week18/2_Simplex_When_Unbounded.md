# Simplex Algorithm when the Solution Space is Unbounded
#SimplexAlgorithm 
* There is no solution to a linear programming problem when the solution space is unbounded. 
* Thus this needs to be detected by the simplex algorithm to return an error.
* This can be done in the choosing of the leaving variable (step 4 in [[1_Simplex_Algorithm]]) wherein if all choices of the `slack_variable ÷ basic_variable` are negative, then the solution is unbounded.