![[Pasted image 20240207160524.png]]
## Why Do we need Multicore Processors? 
* The magnitude of speed increases in single core processors has decreased significantly due to:
	* Power consumption and heat dissipation.
	* Architectural approaches to increasing processor speeds have been exhausted.
* Hence increasing the number of transistors has come with using multiple cores.

## Challenges with Multicore Processors
* It is hard to program multicore processors as we need to decide:
	* How are processors connected.
	* How is the memory organised.
	* How do they access the memory.
	* How are the cores connected to each other.

## Dennard Scaling
* A law that states that as transistors get smaller, their power density gets smaller such that power use stays in proportion to area.
* Dennard Scaling was accurate until the mid-2000s after which high current leakage and other quantum effects increased the amount of power used per unit area.