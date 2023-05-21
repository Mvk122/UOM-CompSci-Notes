> This is done in-depth in week 6 onwards of System Architecture
# Instruction Scheduling
* Instruction scheduling is done to improve parallelism that is used in serial code through #pipeLining to prevent #pipelineStalls .
* Eg doing all load instructions at once as load instructions could take multiple clock cycles hence by doing them all at once then arithmetic, there are fewer pipeline stalls as the first arithmetic operation (who's variables were loaded first) can be executed in parallel while the following loads continue their operation.
* A challenge with instruction scheduling is that register allocation interferes with it. If allocation has to spill registers, the schedule can change as the weights of nodes change.

## Precedence Graph
![[Pasted image 20230521045823.png]]
* Precedence graphs are data dependence graphs that can be used for instruction scheduling.
* Each node in the graph will have a weight that is the longest delay to reach one of its leaf from it.
* A schedule can then be created wherein at every cycle, look at the ready instructions and schedule the instruction with the highest weight.
* There are other alternatives to this form of list scheduling:
	* `Forward List Scheduling`: Start with all available options and work forward in time. 
	* `Backwards List Scheduling`: Start with leaves and work backwards in time. 
* The best option is to do both and keep the better option.