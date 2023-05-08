#multiCoreSystems
# Multi-Core Systems
## Motivation for Multi-Core Systems
* Improvements to single-core architectures such as `caches`, `pipelines`, `superscalar`, `out-of-order processing`, `multithreading` etc have limited scalability as hardware, power and cost increase more than linearly while performance improvements increase less than linearly.
* Reasons for this relationship of cost to benefit include: 
### The Power Wall
* Power dissipation can be calculated with `Power = CapacitiveLoad * (Voltage^2) * Frequency`.
* Increasing the clock speed means more power is dissipated.
* Decreasing the voltage reduces dynamic power consumption but increases the static `power leakage` from transistors which is the main contributor to power consumption.
* More watts per unit area means that cooling becomes a serious problem as expensive bulky cooling will be required which is not practical for all form factors.
### Limited Instruction Level Parallelism (ILP Wall)
*  The implicit parallelism between instructions in 1 thread is limited in many applications.
* The hardware also poses limitations in terms of:
	* Instruction window size for #outOfOrderExecution .
	* Number of instructions that can be fetched per cycle.
### Memory Speeds
* Historically, memory has not gotten faster at the same rate as processors.
* This has lead to CPU utilisation in memory intensive applications to be as small as 10%.
### Architectural Complexity
* It is hard to innovate on processor architectures as their complexity is already so vast.
### Transistor Unreliability
* Smaller transistors have less predictable characteristics due to physical properties like quantum tunnelling.

## Multi-Core System Choices 
* A solution to the above problems comes in the form of multi-core systems wherein multiple parallel less complex cores are used to boost computing speeds.
* This has its own design decisions however:
### Independent vs Distributed Memory
* Distributed memory has generally won out however there are pros and cons for either solution.
#### Independent Memory
* Independent memory per core is simpler and can be faster.
* It is more difficult to program for as communication between cores needs to be explicitly coded.
* The code will thus need to be changed for each different CPU configuration with different amounts of cores and memory hierarchies.
#### Distributed Memory
* At the software level, processors have the same view of memory.
* Communication is implicit so programming is easier.
* However, to prevent desynchronization issues, only 1 core should be able to access the same memory location at once. This can lead to bottlenecks. 
