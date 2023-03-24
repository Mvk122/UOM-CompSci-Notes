# Main Memory

## Content Addressable Memory / Associative Memory
* Returns the address for the data given the data as an input.
* Is not directly part of the main memory hierarchy and is used as a component in other memory models:
	* Highly associative caches.
	* Packet routeing and lookups.
	* AI/ML acceleration.
	* Used for branch prediction.
* Usually built out of SRAM.

## Dynamic RAM
![[Pasted image 20230323190714.png]]
* Extensively used as the main memory in systems.
* Very compact and has the most bits per area of RAM.
* Has moderate power needs (more than SRAM).
* It is not completely randomly accessible as the timing of reading and writing consecutive columns in a row is faster than reading and writing to random rows and columns This is due to the operations of DRAM:
	* A single row is activated and stored in the row latch. This destroys the memory in the row.
	* One or many columns of this row can be read or written to sequentially as many times as required.
	* The memory in the latch is now stored back in the row.
	* Thus it is faster (lower latency) to read and write within the same row as the activation and storing of the row only needs to occur once.

### DRAM Burst Access
* Due to the activation and subsequent deactivation of a row taking a large amount of time, combined with general spatial locality, DRAM can act in a burst mode wherein when a row is opened, as much of the row is read as possible at once to fill in a cache line before closing the row.

## Synchronous DRAM (SDRAM)
![[Pasted image 20230323200219.png]]
* The modern way to interface DRAM.
* Uses a clocked wrapper to make timing/ interfacing easier.
* Provides high bandwidth burst access however it still has a long latency and scheduling issues.
* It may contain multiple DRAM arrays (Banks) that are independent and access is shared via a time shared interface.
* Due to the banks being independent, multiple operations can interleave.
	* To help with this, `low-order` address bits can be used for the banks to allow the banks to interleave as many addresses close together are used at once.
	* However in a multi-core system, using `higher-order` bits for banks is more appropriate as addresses would arrive in several different banks roughly simultaneously.
* Has a controller for scheduling and interleaving requests between the many banks.
	* It translates bus operations into appropriate commands for the SDRAM chips taking into account the RAM's timing characteristics and clock speed.

### SDRAM Line Closure
* After an SDRAM burst has occurred, there is a decision to be made as to if the row should be closed before the next operation.
* Closing it reduces latency for the next access if a different row is used, however the latency becomes much higher if the next access wants the same row.

## DRAM Hardware Specifics
* DRAM must be refreshed periodically, every row in the bank must be activated and then precharged every few milliseconds.
* The controller has to synchronise returned data with internal delays.