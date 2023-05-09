# Data Centres
## Amdahl's law
![[Pasted image 20230509023445.png]]
* Estimates a parallel system's maximum performance based on the available parallelism of an application.
* Initially used to discourage parallel architectures however it has now shown that S normally remains constant whereas P depends on the size of the input data. 
* Thus to increase the proportion of parallelism, in general you need to increase the size of your dataset.

## Data Centres
* Generally have a lot of CPUs on a lot of motherboards and are focused on many applications:
	* `High Performance Computing`: Running 1 large task as quickly as possible.
	* `High Throughput Computing`: Running as many tasks per unit of time as possible.
	* `Big Data Analytics`: Analysing and extracting patterns from large, complex data sets.
* Are generally optimised for cooling and power efficiency with high redundancy for fault tolerance.

## Alternative High-Performance Architectures
### Intel Xeon Phi
* All logic is connected through a bidirectional ring.
* Caches are coherent through a distributed directory.
* Local RAM needs to be updated with the host RAM through PCIE (Is an add-in card).
* Used for high-throughput computing using many smaller cores.
### Single Instruction Multi Data
* Performing the same operation over many data at the same time to reduce instruction memory pressure.
* Can achieve huge speed ups for adequate workflows.
* However there are performance limiting issues in terms of: 
	* Evaluating conditionals 
	* Loop dependencies
	* Non-sequential data
	* Memory indirection
### General Purpose GPUs
* Massive throughput however since it is based on arrays of cores executing the same instructions over different data:
	* Control operations are slow as they need to be executed on all cores.
	* Memory accessed by all cores needs to be consecutive.
	* The programming model differs significantly from the standard sequential model.
	* Moving data from/to memory is very expensive.