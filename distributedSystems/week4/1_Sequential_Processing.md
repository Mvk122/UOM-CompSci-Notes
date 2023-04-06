# Sequential Processing

* Machines make storage and compute resources available.
* An operating system's function is to make the most efficient allocation of compute and storage resources to the various processes that is is running.
* The OS does so by:
	* Creating an address space for each process. 
	* Allowing for the sequential reading of steps that comprise the process.
	* Ensuring that other processes are not able to modify the memory of a process.

## Limitations of Sequential Processing
![[Pasted image 20230406202853.png]]
* Each of the functions foo and bar may take too long to compute to have them done sequentially due to being either: 
	* Computationally intensive.
	* Having to wait for another slow peripheral/ external process to complete.
* Sometimes the processing cannot be done on the host machine due to limitations on the machine's memory.
* Sometimes the processing must be done in another machine due to proprietary restrictions. 

## Benefits of Non-Sequential Processing
* The ability to process `concurrently` in different processes so while one process waits on a peripheral, the next process can be worked on.
* The ability to process in `parallel` in different processors to speed up the computation.
* 
