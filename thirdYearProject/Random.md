* Project is to develop simulators not to create accelerators

## Kostas PHD Summary
* The question: How can we add custom compute kernels to the processor to speed up computation and where would we add it within the cache memory hierarchy of an SOC.
* To gauge their performance, we need to create a simulator to place RTL kernels in different places in an SOC and compare their performance differences.

## Kostas PHD Questions
* What is a functional/timing partition simulator and how can it be faster and more accurate than other simulators?

## Project with the same Background
https://www.sciencedirect.com/science/article/pii/S1569190X20300265
## Project Plan Thoughts
* Based on the [description of SimAcc](https://ieeexplore.ieee.org/document/8735519)  it is a functional/timing partition simulator that runs on FPGAs to get more accurate simulation results and in a faster time than software based simulators.
* Furthermore, based on the [PHD paper sent](https://pure.manchester.ac.uk/ws/portalfiles/portal/267869497/FULL_TEXT.PDF), the simulator also works for hardware accelerated ArmV7 binaries.
* Though the wording is slightly ambiguous to me. By hardware accelerated do you mean for any FPGA hardware that could be made or only for standard ones like GPUs and video encoding/ decoding.
	* In the case where it means that it only does standard ones, I think the plan would then be to create the FPGA code for one of the algorithms/methods (XGboost or spiking neural networks for example), then extend SimAcc to simulate them and use the simulation to improve performance.
	* However in the case where it means that it handles all hardware acceleration, the step to create the simulator can be skipped. However I am unsure if this will have enough scope for the 19 weeks of work or if it is in the spirit of the project plan wherein:
		* `The second phase will involve a significant development effort using FPGAs to implement part of a simulator or prototype a novel hardware feature.`


# Which HDL language should be used for the project?
## Chisel
### Pros
* Is in a higher level language, could make development easier. (Scala).
* Has a decent tutorial.
* Compiles down to verilog so it can theoretically be used on any FPGA.
### Cons
* Won't have as many online resources as it seems to be the least popular option.
* Might not be supported by Vitis natively.
* Could be hard to integrate with SimAcc (not sure as I don't have the SimAcc code).
* Seems to wrap around verilog primitives directly instead of abstracting that away and exposing object oriented interfaces, this could make development as slow as if plain verilog was used.

### HLS Catapult
### Pros
* Much more mature than Chisel
* Abstracts away the verilog code into object oriented patterns, making it easier to develop with. 
### Cons
* Seems to be a closed source software by siemens, so getting support/ documentation without being one of their customers might be very hard.
