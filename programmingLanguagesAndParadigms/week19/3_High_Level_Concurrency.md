# High Level Concurrency
* Even with message passing and mutual exclusion, there are still high level bugs with concurrency that cannot trivially be solved: 
	* `Deadlocking`: All processes are waiting for other processes to leave the critical section, there is no way to exit the deadlock other than for processes to detect the deadlock and release their resources. 
	* `Livelocking`: Cycle of processes try to enter a critical section but they all fail. 
	* `Thread Starvation`: Processes cannot progress hence wait forever to enter a critical section.

## Solutions to High Level Concurrency Problems
### Formal Reasoning 
* A formal description of the program can be used for automatic bug discovery.
* The description needs to have properties dictating:
	* `Safety Properties`: Properties that should always be true.
	* `Lifeness properties`: Properties that should eventually become true 
### Transactional Memory
* Like database transactions but for memory wherein regions are marked as atomic.
* Like a database, data read or written to the region must not be written or accessed for elsewhere.
* If atomicity is violated, a rollback process occurs.
### Automatic Concurrency
* Concurrency that is handled by the programming language. 
* It is hard to do in most programming languages as most languages require a sequential order of semantics.
* It can be done by tracking memory accesses to do speculative parallelism wherein the code is run in parallel and memory access is tracked to verify correctness.
* It is better done in functional languages as functions have no explicit ordering, have no state and data flow is explicit.