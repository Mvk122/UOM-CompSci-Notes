# Coarse Grained Multi-Threading 
* Executes a single thread continuously, only switching in the case of: 
	* An expensive operation (cache misses)
	* After a `quantum` (certain amount) of execution.
* Requires a fast switching mechanism (not necessarily instantaneous) as the switching needs to be a better alternative than waiting for the cache misses to resolve.
* Prevents delayed execution of threads as opposed to fine grained multithreading as threads are run until there is a stall as opposed to interleaving threads regardless of stalling.

## Thread Switching on misses
* Due to pipelining([[1_Introduction_To_Pipelining]]), thread switching has complications as operations further in the pipeline need to be cancelled when switching unexpectedly.
### Switching on Instruction Fetch Misses
![[Pasted image 20230416134030.png]]
* When there is an instruction fetch miss on instruction C, we can just remove it and switch to another thread.
### Switching on Memory Miss
![[Pasted image 20230416134132.png]]
* The pipelined instructions after the miss need to be removed.
* The PC of the blue thread needs to be rolled back to instruction a.
* Switch to the orange thread.



