# Hardware Multi-Threading

## Hardware vs Software Multi-Threading
![[Pasted image 20230416122552.png]]
* Hardware multithreading allows for greater parallelism as instructions between processes are independent hence there are no data-dependencies limiting parallelism.
* Thus hardware multithreading allows for several threads to share a single processor at the cost of hardware replication to store independent thread state: 
	* Registers
	* Program Counters
	* Translation Lookaside Buffers.
* Thread switching is much faster as context does not need to be loaded and stored.
* This is opposed to software multithreading which allows for the appearance of several processes/threads running concurrently through interleaving.

## Thrashing due to Multi-Threading
* Given that caches are shared between multiple hardware threads, thrashing can occur if 2 threads are accessing independent regions of memory which occupy the same cache lines.
* This can come from: 
	* Thread A loads memory address 0, putting addresses 0 to 8 in the cache
	* Thread B loads memory address 4, since it is a different thread, it replaces the value that was set by thread A, caching values 4 to 8.
	* Thread A loads memory address 4 but its cache has been invalidated and replaced by Thread B, thus another cache miss has occurred.
	* The above cache miss would not have occurred if Thread B did not load an adjacent address to the one used by Thread A.