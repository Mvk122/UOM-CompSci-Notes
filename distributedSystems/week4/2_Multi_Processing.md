# Multi Processing

## Multiprocessing vs Multitasking vs Multithreading
* `Multitasking` refers to using a scheduling policy to `time-slice` different processes on a processor, allowing for processes to interleave. This gives the appearance of concurrency but nothing is being done concurrently. This is helpful in more I/O bound operations wherein one process is waiting for an I/O operation before continuing.
* `Multiprocessing` refers to actually running different processes in parallel with their own distinct memory spaces. Hence if there are multiple cores, the process can compute results faster.
* `Multithreading` refers to running many concurrent executions of the same process in parallel (in the case of multicore systems, it can still be done on single core systems just not concurrently). Multithreading is different than multiprocessing as multiple threads will be able to share the same memory.

## Multi Processing
### Multiprocessing by Forking 
* Refers to creating multiple copies of a process to execute them concurrently.
* The child process is given a distinct copy of the parent's address space however making copies is quite expensive.
* This is used often in client server applications where the server creates a new fork for every client that joins.
### Multiprocessing by Threading 
* Refers to creating multiple threads of execution of a process without copying the memory hence the parent and child share the same memory.
* This is less safe but more efficient than forking.

## Concurrent Processing 
* Having many running processes in parallel where processes are often threads.
### Concurrent Processing by Parallel Computing 
* There are many processors bound by an interconnect with true parallelism in execution.
### Concurrent Processing by Distributed Computing
* There are many independent, self sufficient, autonomous and heterogenous machines that work together to compute many tasks.
* The separation of machines means communication over the network which can be slow. 
* Message exchanges are done on a middleware API to reduce communication complexity.
