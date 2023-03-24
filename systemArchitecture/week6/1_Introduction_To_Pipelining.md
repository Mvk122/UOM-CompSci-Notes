# Introduction to Pipelining
![[Pasted image 20230324062250.png]]
* The worst case scenario for any instruction has 5 stages, split into the fetch execute cycle:
	* `Fetch`: Instruction Fetch (`IF`), Decode Instruction and select registers (`ID`)
	* `Execute`: Perform operation or calculate address (`EX`), access memory (`MEM`), write to a register (`WB`).
* Since these instructions use separate parts of the processors in the ideal assumption that each instruction takes one clock cycle, multiple instructions can be run simultaneously using pipelining.
* The above is for a 5 stage pipeline, however modern processors can have up to 30 stages, this comes at the cost of:
	* Extra hardware.
	* A more complex design.
	* Difficulty to split the stages into uniform size chunks.
	* A higher probability of hazards occurring and worse penalties when they happen.

