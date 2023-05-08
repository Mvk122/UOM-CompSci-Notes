# Directory Protocols
#directoryProtocol
* Cache line information is stored in a separated subsystem and changes are updated there.
* Is better than #snoopingCoherencyProtocol in systems with a larger number of cores (more than 8-16) as it is more scalable by using distributed hardware.
* The memory system has a directory which stores information of what is being shared.
* This allows for coherence messages to be `point-to-point`.
* More messages will be required per operation but many messages can be transmitted in parallel.

## Directory Protocol Implementation
![[Pasted image 20230508183641.png]]
* Cache lines will have one of 3 states:
	* Invalid
	* Shared
	* Modified
* The directory also has a state for each cache line: 
	* Not Cached
	* Shared: Not modified and in at least 1 core.
	* Modified: Modified and in 1 core
* The directory also has a `sharing vector` to know which cores have copies of each cache line.
* The directory sits between the caches on an interconnect.
* Cores only have to communicate to the directory and the directory knows which cores to communicate with due to the `sharing vector`.

## Distributed Directories
![[Pasted image 20230508183907.png]]
* The directory, though more scalable than #snoopingCoherencyProtocol has become another centralised performance limiting piece of hardware.
* To alleviate this, multiple directories can be used however the cores need an extra bit for each cache entry to state which directory its `home` is in.


