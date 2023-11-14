# Simulation Time
* Time in verilog is discrete but multidimensional.
* The resolution of the discrete time can be controlled.
* It is multidimensional as there are: 
	* Simulation and delay specification (Time Dimension), representing the discrete steps during simulation and the delays that are specified within the code.
	* The Event Queue (Event Dimension): The simulation maintains an event queue that orders events based on their scheduled time.
* Since things can happen simultaneously in a given timestep, the result can be either predictable or unpredictable.
* All blocking assignments are done before non-blocking assignments.
## Predictable in Simulation Time
* Blocking assignments in the same block.
## Unpredictable in Simulation Time
* Blocking assignments in different blocks.