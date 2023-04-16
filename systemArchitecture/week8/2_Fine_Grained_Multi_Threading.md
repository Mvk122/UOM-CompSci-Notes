# Fine Grained Multi-Threading
![[Pasted image 20230416123711.png]]
* Fetches an instruction from a different thread in each cycle generally in a round-robin manner.
* Required instantaneous context switching.

## Benefits of Fine Grained Multi-Threading
* Helps to avoid dependencies within a certain thread by switching to a different thread in each cycle.
* Takes pressure off of Forwarding ([[3_Data_Hazards]]) by having a gap between instructions in the same thread as another instruction from a different thread is done in between.
![[Pasted image 20230416124452.png]]
* In the case of an instruction fetch miss in one of the threads, instead of switching back to the missed thread after a round of the round-robin, the processor can continue to do instructions in the same thread while the miss is resolved.
* Furthermore, if executing out-of-order, a thread can be ignored while it is stalled.

## Disadvantages of Fine Grained Multi-Threading
* Execution of an individual thread may take longer as even if a thread can execute with no stalls, instructions from other threads will be interleaved within its processing. 