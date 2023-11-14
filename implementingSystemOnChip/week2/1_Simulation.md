![[Pasted image 20231110143500.png]]
## What Simulation Requires
* The high level modelling should be complete.
* Block relationships exist.

## What Simulation Doesn't Require
* Cycle-accurate timing/ implementation.

## Simulation Detail 
* To finalise an ASIC design, different levels of simulation must be performed, each requiring increasingly detailed models to perform:
	* Functional: Verifies the functionality of an RTL description
	* Timing, Electrical, Physical: The correctness of a manufactured chip and its timing and electrical properties. 

## Functional Simulation 
* Verifies the logic behaviour of the device. 
* Can be assisted by test coverage tools that: 
	* Checks which HDL statements have not been executed.
	* Which branches have not been taken. 
	* Which nodes have not adopted both binary states at least once. (This is difficult with behavioural HDL as there are no nodes).
* Not possible to gain complete timing models, however there is cycle accuracy.
	* This is because functional tests typically use assumptions of synchronous behaviour and that circuit speed is greatly influenced by physical properties.
	* A rough estimate can be made with annotations.
* Can do things that are not easily made into actual hardware eg: 
	* While statements. 
	* The test environment can respond to the state of the device under test without building an explicit RTL machine to do it and wiring up the appropriate connections etc. 


