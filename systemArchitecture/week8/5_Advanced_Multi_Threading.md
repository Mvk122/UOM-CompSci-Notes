## Speculative Execution 
![[Pasted image 20230416144233.png]]
* Occurs when reaching a conditional branch instruction in a pipeline wherein the decision to take the branch has not been decided.
* 2 threads can be spawned, one taking the true path and one taking false.
* Once it is known which is correct, kill the wrong one.

## Memory Prefetch
![[Pasted image 20230416144419.png]]
* Application is compiled into 2 threads, one running the application and a scout thread that only does memory operations.
* The scout thread runs ahead and fetches memory into the cache in advance, thus increasing the cache hit rate tremendously.
* The scout thread needs to be timed properly however:
	* Fast enough that the memory delay is hidden
	* Slow enough that it does not replace useful data from the cache.

## Slipstreaming 
![[Pasted image 20230416144642.png]]
* Split the application into 2 threads:
	* One to run the application
	* One to run the critical path (longest path) of the application
* The slipstream runs the longest operations, passing results back to the original thread, reducing the impact of long-running tasks. 
* However, this requires special hardware.

## Transient Fault Detection 
![[Pasted image 20230416144820.png]]
* When running a block of code that requires reliable computation, create 2 threads running the same computation.
* Compare the result after execution, if it is wrong then either:
	* Rollback execution 
	* Use a majority vote to choose an answer