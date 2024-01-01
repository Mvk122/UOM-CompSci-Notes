# Advanced eXtensible Interface 
* Uses transactions instead of bus cycles.
* More like a network where packets can go from any source to any destination.
* Uses semi independent channels that are unidirectional and may be pipelined.
* It is more extensible however latency can be many cycles.
* Throughput can be increased using data bursts. 
* Can allow for out of order transactions.
* Can be multiplexed and redirected throughout the network using packet IDs for reconstruction.

## AXI Operation
* Since transactions can be out of order and intermixed there is a packet ID on each packet to allow for reconstruction. 
### Write Transaction
* Write command with an address and burst size.
* Burst of write data.
* Response status sent.
### Read Transaction 
* Read command with address and burst size.
* Data burst and status sent in the same response.

# Pipelined AXI
![[Pasted image 20240101184535.png]]
* When valid and ready are asserted, a transfer takes place. This has a much lower latency than a handshake mechanism.
* Since packets can get stuck on some phases (i.e a wait signal), there is a challenge on when to assert ready: 
	* Option 1: Assert ready only when the block is empty and ready to receive data. This option is too slow as it requires the ready signal to be propogated through the pipe
