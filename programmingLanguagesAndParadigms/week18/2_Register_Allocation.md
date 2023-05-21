# Register Allocation 
* Register allocation needs to be done to minimise the use of registers by functions to ensure that the amount of calls to memory are minimised.
* There are register allocation methods for both `local register allocation` and `global register allocation`.
* Modern processors may have multiple register classes for different data types.

## Basic Blocks and Life Ranges
* A maximal segment of straight-line code with only 1 entry point (no jumps to the middle of it) and one exit point. (Only the last instruction leads to a new block).
* The number of registers needed in a basic block corresponds to the maximum number of active `live ranges`.
* A variable is live between its definition and its last use.
![[Pasted image 20230521043406.png]]
* Above shows the values, the registers they're in and the ranges in which they are live for.
* Note that if a live range starts at an instruction that another terminates, the same register can be used for both hence the number of live ranges at that point can be deducted by 1.

## Basic Local Register Allocation
### Top Down Register Allocation
* Reserve registers for the most frequently used values and get all other values from memory.
* This is not ideal as values could be heavily used in one section of the code but not another.
### Bottom Up Register Allocation
* Keep a pool of registers and assign a register when a value is initialised. and return the register to the pool at the end of the live range.
* If a register needs to be allocated but the pool is empty, evict the register that is used furthest in the future to make space for the new value to be allocated.

## Graph Colouring Register Allocation
* Live ranges that do not interfere can share the same register hence we can:
	1. Build an interference graph
	2. Construct a k-colouring of the graph where k colours are used.
	3. If a colouring cannot be created with only `k` colours, choose values to spill and repeat from the start.
	4. Map the colours onto physical registers.
* Mapping can be done in a `top-down` approach wherein the ranges are ranked by some heuristic and following the ranking, for each node pick the first colour that is not used by the node's neighbours.
* Heuristics to be used can be:
	* The number of neighbours
	* Spill Cost
