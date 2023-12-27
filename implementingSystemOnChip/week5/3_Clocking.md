## Definitions
* `Metastability`: Flip flops can be a 1, 0 or metastable aka in between. This can come as a result of violating set up/ hold conditions. In principle a flip flop can remain metastable forever but if it starts to resolve one way, positive feedback pushes it further in that direction.

## Clock Distribution
![[Pasted image 20231227165833.png]]
* A H-Tree is used to distribute the clock signal, ensuring that each component in the chip is connected at the same "level" of the tree to minimise clock skew.
	* `Clock skew`: The difference in arrival time of the clock signal from one part of the processor to another.
* Generally the high fan-out requires amplification/ buffering as:
	* Clock edges should be fast to decrease the uncertainty in when the transition occurs.
* The amplification/ buffering strategy works as:
	* Clock signals are repetitive so the latency doesn't matter. 
	* They always arrive at regular intervals.

## Timing Closure
![[Pasted image 20231227174131.png]]
* Fitting all the logic into the desired clock period.
* Can be assisted by `static timing analysis` tools which deduce the logic paths by finding the registers and estimating the signal delays through all paths.
	* This gives a conservative upper bound but can be too pessimistic.
* The output is the slowest path which is the limiting factor in the circuit. Finding this critical path can be hard to achieve through simulation, however as it is not guaranteed that the critical path is simulated.

## Clock Domains
* It is not possible to always have a single clock as:
	* Synchronous clock distribution can be increasingly difficult.
	* Blocks may work optimally at different frequencies as they may be IP from different vendors.
	* Some I/O may require different frequencies.

## Synchronisers
![[synchroniser.png]]
* Synchronisers allow for signals to be sent between clock domains.
* The first flip flop latches a valid level which the second copies one period later.
* If the first flip flop is metastable, it has an entire clock period to stabilise for the second flip flop.
* If it does not stabilise within the clock period, it will be forced to a digital state on the next clock edge. However, the second flip flop can still be metastable if it was resolving at the wrong moment.
* The ever-present chance of failure from the synchroniser is always present, however designers can reduce the odds of failure by chaining more flip flops.

## Crossing Clock Domains
* When crossing a clock domain, there is always some latency and a chance of failure due to metastability.
* There are many ways to reduce latency and increase throughput however:
![[Pasted image 20231227223657.png]]
* Synchronising Every Item
	* High latency, low bandwidth.
* Buffering packets of items.
	* Longer latency, high bandwidth.
* 