# Secondary Storage
* Storage that is outside the main address space.
* Is usually used for either `filing systems` or `page stores`.
* Various technologies are used eg `magnetic disks`, `optical disks`, `SSDs`.

## Disks
* Spinning platters with a read/write head.
* Usually in stacks that use both sides.
* Bits are encoded by polarisation of domains on the surface.
* Data storage is organised into blocks.
* Latency is usually inconsistent and based on where blocks are on the drive as it is dependant on how long the read/write head takes to reach the block from its current position.
	* Hence to improve performance, files that are used most often are usually placed physically closer together on disk.
* Bandwidth is usually dependant on disk rotation speed and data density, it is reduced if the data is fragmented.

## Disk Fault Tolerance
* `Cyclic Redundancy Checks`: Used as a block code, can only be used for error detection.
* `Error Correcting Codes`: Uses parity bits to detect errors as well as correcting them.
* When the above methods are unsuccessful, bad sectors are remapped so faulty parts of the disk's surface are not used.

## RAID (Redundant Array of Inexpensive Disks)
* Techniques to use multiple drives to improve either the reliability or performance of storage based on an array of disks.
### RAID1
* The same data is mirrored on many disks.
* Is much more fault tolerant as the data is replicated.
* Has higher bandwidth for parallel reads. 
* No performance increase for single requests, no latency improvement either.
### RAID0
* Data is striped across the many disks.
* Much higher bandwidth as data access is parallel.
* Much more likely to have faults as one disk failing means the entire system fails.
### Nested RAID
* Hybrid systems that use nested arrays of RAID setups.
* Eg RAID01: RAID1 array of RAID0 systems.

## Disk Interconnection
* Disks are usually connected to the CPU using the following interconnects:
	* `SATA`: Uses a serial bus interface with up to 6Gb/s bandwidth.
	* `PCIe`: Offers transfer speeds up to 7.5 GB/s per lane.

## Disk Caches
![[Pasted image 20230413183410.png]]
* Also called a `disk buffer`.
* Are stored on the disk itself and can save pages, acting as a write buffer.

## Solid State Drives
* Are permanent non-volatile semiconductor stores, typically using flash memories.
* They have no moving parts, making them robust, quiet and compact.
* They usually have lower latency when reading and are random access hence the latency is unchanged regardless of the address sequence requested.
* However, they have lower long term data retention and a limited number of write operations.