# Write Buffers
![[Pasted image 20230218120749.png]]
* When writing to memory, there is no need for the processor to wait for the write operation to complete.
* Hence write requests can be written to a write buffer that is slowly written to memory.
* Since read operations require the processor to wait, read operations should be allowed to overake queued writes.
	* This `out of order execution` can be problematic however, if data is being read while writes to the same data are currently within the write buffer. 
	* However, it can be resolved by also looking up within the write buffer when doing a read. If the write buffer contains the corresponding memory, the memory operation is cancelled and the value from the write buffer is `forwarded` to the processor.
* Generally write buffers are a `FIFO` queue.
* Works for most RAM however out of order execution can cause problems with `memory mapped I/O` or `shared memory` as acknowledgement for previous writes (done through an out of order read) can be mistaken for acknowledgements of writes stuck in the write buffer.

## Solving Problems with Out of Order Execution
### Disallow Buffering
* Pages may be marked in the page table or addresses can be recognised by the hardware as addresses to disallow buffering.
* Thus writes to these addresses must be complete before the processor continues.
* This requires a `write response` to tell the processor that the write has completed.
* Has a performance penalty.

### Memory Barrier
![[Pasted image 20230218120816.png]]
* Writes to the memory mapped I/O creates a `barrier` wherein all preceding operations must complete before any succeeding operations start.
* Hence more writes can be sent to the write buffer and the processor can continue operations however read operations must wait for the barrier to pass, thus stalling the processor until the barrier passes.
