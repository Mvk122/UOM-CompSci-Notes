# Sequential Consistency
Is a consistency model wherein: 
	* Memory operations appear to execute one at a time.
	* All threads see write operations in the same order.
	* Operations in 1 thread appear to execute in the order described by the program.
* Requires the use of special instructions: 
## Fence
![[Pasted image 20230508161422.png]]
* All memory executions before the fence need to complete before executing the ones after.
## Barrier
![[Pasted image 20230508161501.png]]
* All threads need to reach the barrier before operations can continue.
## Locks
![[Pasted image 20230508161749.png]]
* Only one thread can proceed to the atomic section. 
* Requires support from the hardware as the read, compare then write of the lock-flag needs to be atomic, otherwise another thread could think the lock is available if its read operation is between the read and write operation of another thread.
* Hardware support comes in the form of: 
	* Atomic compare and swap instructions.
	* Load linked and store-conditional instructions wherein:
		* `Load Linked Instruction` : Hardware locks the cache line and returns its contents.
		* `Store Conditional`: Only allows stores to the memory location if no changes have been done to it since the Load Linked Instruction.
	* Transactional Memory wherein the atomic sections are executed assuming there will be no conflicts. Detect for conflicts after the operations and: 
		* If conflicts, roll back and start over.
		* If no conflicts, commit the changes.
