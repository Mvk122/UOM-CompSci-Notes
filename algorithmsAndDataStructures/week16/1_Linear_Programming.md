# Linear Programming 
#linearProgramming
* Linear programming is an optimization strategy to minimize or maximize a variable given a set of constraints.
* The constraints have their own constraints: 
	* They must be expressed as a linear relationship eg $a_1x_1 + a_2x_2$. (No squares or cubes allowed).
	* The constraints are inequalities. 
		* the = sign is not allowed.
		* It must be of the form `variables (< or <=) constant`.
	* All variables must be greater or equal to 0.

## Representing LP Problems with Graphs
* Linear Programming problems can be represented on graphs where the axes on the graph correspond to the variables that can be changed to create a solution.
* Constraints can be represented by their standard form notation on the graph eg x < 5.
* The possible solutions can be represented by the area under the graph. The example below has the constraints: 
	* x < 5.
	* x and y can be changed but they must sum to less than 6.
![[Pasted image 20230425150338.png]]
* Any solution where both the blue and red apply is a valid solution.
* The moveable slider shows the summation of x and y to a total value. As it moves up, it intersects with the different points on the graph until the entire line is above the range of feasible solutions. 
* The best feasible solution always exists at the intersection between different constraints.

## Converting to Standard Form
### Removing "=" Sign
* $=$ is not allowed as a constraint, this can be remedied by breaking an equals statement into 2 statements using $<=$ and $>=$ eg:
* $x = 5$ becomes $x <=5$ and $x >= 5$
### Removing ">" and ">="
* Constraints have to be less than or less than or equal to. 
* To convert statements, negate them.
* Eg $x > 5$ becomes $-x < -5$.