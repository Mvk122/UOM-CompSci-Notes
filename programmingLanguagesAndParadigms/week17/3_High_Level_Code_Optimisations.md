# High Level Code Optimisations 
* Make optimisations on the code at different stages in the compilation process to improve program performance and reduce the size of the code.
* It is restricted wherein:
	* It must preserve the meaning of the program.
	* It must improve performance in the average case.
	* The time taken to compile must be justified.
* It can be done in different stages:
	* Source Code 
	* IR Level (Machine dependent)
	* Target code (Machine Independent)

## Common Code Optimisations 
### Copy Propagation
* After a copy statement eg `x=y`, try to use y as far as possible.
### Constant Propagation
* Replace variables that have constant values with their values to prevent memory accesses.
### Constant Folding 
* Deduce that a value is constant and replace it with the constant instead.
### Dead-Code Elimination 
* If a code branch or value is never used, remove it from the compiled code.
### Strength Reduction 
* Replace expensive operations with cheaper ones
### Loop Invariant Code Motion 
* Detect statements inside a loop who's operands are constant and move them out of the loop to prevent them from being done multiple times.
### Loop Unrolling
* Replicate the loop body inside the loop, and change the increment to be a multiple of its previous value to compensate. 
* This helps with out-of-order processors that start the next instruction before the previous is completed and by reducing the amount of branching, the amount of "instruction misses" are reduced.
