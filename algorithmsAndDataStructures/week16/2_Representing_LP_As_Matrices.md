# Representing Linear Programming Problems as Matrices
#linearProgrammingMatrices
* Create a list of constraints where the variables are in the same order eg: 
	* $x_1 + x_2 + x_3 <= 5$
	* $2x_1 - x_2 + 5x_3 <= 7$
* Get the equation for what needs to be maximized eg: 
	* $5x_1 + 7x_2 - 3x_3$
* There are 3 relevant matrices that each correspond to one of the following:
	* We want to maximize $c^Tx$
	* We have constraints $Ax <= b$
	* We require that $x >= 0$
* Thus the matrices are as follows:
![[Pasted image 20230425155900.png]]
* The first is the order of the variables 
* C refers to what needs to be maximised
* b refers to the right hand side of the constraints
* A refers to the left hand side of the constraints in order.