# 1a
* Due to manufacturing discrepancies, it is impossible to make accurate delays.
* Delays should only be used in circuits to emulate delays from real components, simulate I/O or for aesthetic reasons.

# 1b
* When there is a variance in the clock signal's edges from their ideal position.
* The maximum allowable jitter is subtracted from the timing budget as jitter can cause a period to be too short, violating hold time constraints.

# 1c
* Test coverage in verification tries to ensure that every:
	* Branch
	* Line of code 
	* Path 
* Is executed to ensure that the device functions as the designer intended
* Verification checks for manufacturing defects and aims to test that every component is functional as well as ensuring that every component adheres to the requirements:
	* Timing 
	* Heat
	* Power 
	* Electrical 

# 1d
* The time after the clock that the data needs to be stable for the flip flop to read the value.

# 1e
* It is to tell the synthesizer that in the default case, we don't care what the output is. This prevents it from creating a latch.

# 1f
* The short circuit power dissipation wherein during switching, both pmos and nmos are conducting hence current goes from VDD to ground.
* Current required from resistance when switching.