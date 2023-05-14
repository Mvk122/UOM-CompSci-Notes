# Thread Based Concurrency
* Threads are streams of computation communicating through shared state (generally shared memory).
* Due to concurrency, the order of operations on a particular memory address can be essentially random hence making the output random too without proper concurrency control mechanisms for `mutual exclusion` of resources.
## Concurrency Control Mechanisms (Mutual Exclusion)
### Critical Sections
* Critical sections are sections of the code dealing with shared state. 
* They must be mutually exclusive (running on at most 1 thread at once) to prevent non-deterministic behaviour.
* They require a `preprotocol` and `postprotocol` wherein:
	* `Preprotocol`: Confirming if it is safe to enter a critical section.
	* `Postprotocol`: Announcing to other threads that it is safe to enter.
* To prevent multiple threads from entering the critical section at once, the `preprotocol` needs to be atomic. This is usually supported by hardware `compare-and-swap`.
![[Pasted image 20230514214046.png]]
## Higher Level Mutual Exclusion
* `Control-and-Swap` is useful for lower level programming however it can be extended to be more portable, safer and OS-aware.
### Locks
* Locks are an extended form of `Control-and-Swap` that expose 2 functions:
	* `acquire()`: Asks for access to a critical section, goes to sleep if it is occupied.
	* `release()`: Called when leaving a critical section and wakes up threads sleeping on the lock.
### Semaphores
* Like locks but allows for multiple threads/ processes at once. It exposes 2 functions:
	* `wait()`: Acquire the resource and decrement a counting variable if positive. Otherwise go to sleep
	* `signal()`: Release the resource, increment the counting variable if positive, otherwise wake up a thread.
* The counting variable is used to determine how many threads are using the resource at once. 
* The positive value of the count signals how many more threads can access the semaphore.
### Monitors
* Similar to a semaphore but handles the mutual exclusion for an object.
* It exposes 2 functions: 
	* `wait()`: Called when a condition is false. The thread that called it joins the waiting queue, releases the monitor lock and goes to sleep.
	* `signal()`: Called by another thread when it makes the condition true, it wakes up the front of the waiting queue.