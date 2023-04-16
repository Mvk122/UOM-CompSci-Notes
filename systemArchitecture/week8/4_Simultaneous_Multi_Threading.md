# Simultaneous Multi-Threading
![[Pasted image 20230416143343.png]]
* Is used to exploit instruction level parallelism and thread level parallelism at the same time by scheduling as many `ready` instructions as possible in a superscalar processor.
* Implemented mostly in out of order processors because they are able to exploit parallelism. 
* Has a significant hardware overhead however it is less than adding more cores:
	* Replication of thread state.
	* Operand reading and result saving.

## SMT Design Considerations
* Which threads to issue instructions from? 
	* To prevent thread starvation.
	* To maximise overall computational throughput.
	* How much granularity should be chosen given a static policy like round robin (eg 1 instruction per thread vs 2)
	* Which dynamic policy to choose: 
		* Favouring threads with minimal in-flight branches
		* Favouring threads with minimal outstanding misses
		* Favouring threads with minimal in flight instructions

## SMT in In-Order Processors
* SMT is usually used in OoO processors as it can run into the following issues with in-order-processors:
### Asymmetric Pipeline Stalls 
![[Pasted image 20230416143940.png]]
* When pipeline 0 stalls due to a data dependency, pipeline 1 should be able to continue however superscalar in-order pipelines need to advance at the same pace hence pipeline 1 is stalled unnecessarily.