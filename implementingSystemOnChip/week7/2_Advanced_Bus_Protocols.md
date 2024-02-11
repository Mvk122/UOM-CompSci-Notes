# Advanced Peripheral Bus (APB)
![[Pasted image 20240101164332.png]]
![[Pasted image 20240101164427.png]]
* A simple, slow, single master protocol for low speed peripherals.
## APB Operation
* The protocol operates within a 2 cycles wherein in the first cycle the address is set and on the second cycle, the read or write data is put on the bus:
	* Select is set to high.
	* The address is placed on the address bus.
	* Read or write is set.
	* The above signals are set by the bus master
* In the second cycle:
	* The enable goes high.
	* The read or write data is placed on their respective busses.
## APB Complexity
* Since everything occurs in 2 clock cycles, there is a round trip every bus cycle and thus there needs to be enough time for this to occur. 
* 
## APB Extensions
* There are extensions to the spec such as: 
	* A wait state for peripherals to note that they are not yet ready.
	* An error signal for peripherals to note errors such as: 
		* Invalid memory addresses/ insufficient permissions.
		* Page faults.

# Advanced High Performance Bus (AHB)
![[Pasted image 20240101165110.png]]
* Used for processor busses on medium speed devices (eg ARM9).
* Utilises pipelining.
* Intended to perform 1 transfer per clock cycle.
* Multi-master via centralised arbitration.
* Bus cycles can be extended or aborted.
## AHB Operation
* The operations are as such:
	* The command and address are set in 1 clock cycle.
	* The read/write data from the command on the previous clock cycle are placed on the bus for 1 clock cycle.
	* This allows for a new command to be placed and new data to be output at every clock cycle.
## AHB Complexity
* This requires a more complex operation on the master as on each clock cycle: 
	* It needs to latch in the first input data. 
	* Provide output data if the second cycle was a write.
	* Start the third cycle.
## Slow Peripherals on AHB
* If a peripheral is slow and needs wait states, it does this in the data phase.
* Since the operation is pipelined, all other peripherals need to monitor this because if it was to be addressed next, it needs to know to defer its operations.
