# On Chip Interconnects
* The designs of networks on chips are decided based on ideal trade-offs of:
	* `Bandwidth`
	* `Latency`
	* `Congestion`: The effect on bandwidth and latency of using the network close to its peak.
* The designs of networks on chips can be described using:
	* `Topology`: How cores and networking elements are connected together.
	* `Routing`: How traffic moves through the topology.
	* `Switching`: How traffic moves from one component to the next.

## Topologies
### Bus
![[Pasted image 20230509015057.png]]
* Only single usage at any point in time.
* Is controlled by a clock
* Sender must grab a slot through arbitration to transmit data.
* Throughput is limited as bandwidth is divided by the number of cores.
### Crossbar 
![[Pasted image 20230509015211.png]]
* Area and power scale quadratically to the number of nodes hence it is not scalable.
* Bandwidth can be increased and the effect of congestion can be reduced compared to bus.
### Ring
![[Pasted image 20230509015328.png]]
* Simple but with low bandwidth and variable latency.
### Mesh/Grid
![[Pasted image 20230509015352.png]]
* Reasonable bandwidth, variable latency and very scalable.

## Routing Types
### Minimal Routing
* Always taking the shortest path to a destination.
* Packets are more likely to be blocked due to sharing paths.
### Non-minimal Routing
* Packets can be diverted to avoid blocking.
* Can lead to deadlocks, however.
* Requires more hardware to calculate paths.
### Oblivious Routing
* Fixed paths for any connections.
* Simpler and deadlock free.
* Prone to contention

## Switching
* Allows for data to be split into small packets to allow for time-multiplexing of network resources, thus increasing performance.
### Store and Forward Switching
* A packet is not forwarded until all its phits arrive to each intermediate node.
* Has on the fly failure detection.
* Is low performance as latency becomes `distance  * phits` and large buffers are required.
### Cut-through
* A packet can be forwarded as soon as the head arrives to an intermediate node.
* Performance scales with `distance + phits`.
* Less reliable as failure detection can only occur at the destination.