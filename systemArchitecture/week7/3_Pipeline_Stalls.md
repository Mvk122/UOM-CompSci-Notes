#pipelineStalls
# Pipeline Stalls
* The pipeline for parallel instruction processing can be stalled due to `conflicted instructions` such as:
	* `Cache Misses`: Creating a long wait before finishing execution.
	* `Structural Hazards`: Required resources such as functional units are not available.
	* `Data Hazards`: Dependencies between instructions prevents instructions from being run in parallel.
* This can be avoided with `dynamic scheduling` which schedules instructions that are able to be run immediately.

## Data Dependencies
* Out of order execution creates new types of data dependencies:
![[Pasted image 20230414070000.png]]
