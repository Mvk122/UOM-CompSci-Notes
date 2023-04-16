# Out of Order Execution with Tomasulo

## Data Dependency Definitions
* `True Dependency (Read after Write)` : Instruction A depends on the output of instruction B.
* `Anti-Dependency (Write after Read)`: Instruction A writes in the input of a previous instruction B, we need to ensure that B uses the value of the previous value.
* `Output Dependency (Write after Write)`: 2 instructions write to the same address, we need to ensure that the final value of the data is from the second instruction.

## Tomasulo Principles
*  Uses distributed control to allow for a larger window of instructions than scoreboarding.
* Uses `Reservation Stations` in the functional units to keep track of instruction information.
	* Uses `Register Renaming` in the reservation stations to eliminate WAR and WAW dependencies.
* Uses a `Common Data Bus` to broadcast data and results to the different devices when the data is available.
	* This distributed publishing approach allows for multiple reservation stations to read the value as soon as it is ready.
### Register Renaming
* Changes the destination register that is being used to eliminate WAR and WAW dependencies.

### Tomasulo Process
* Instructions are fed into the reservation stations of their corresponding functional units.
* The reservation stations track operands and buffer them. As soon as the operands are available from the common data bus, the execution occurs.
* Once the execution is completed, the result is placed on the common data bus and any other reservation stations requiring the data are able to read the data and operate on their operands.

## Advantages of Tomasulo
* Multiple instructions can be issued simultaneously if they are waiting on a single result as the result is broadcasted on the Common Data Bus.
* Stalling can be avoided with register renaming.

## Disadvantages of Tomasulo
* The performance is limited by the Common Data Bus as it needs to go to all functional units. This requires a high wiring density.
* The number of functional units that can complete per cycle is limited to one due to the Common Data Bus.
	* Multiple CBDs can be used but more functional unit logic will be required for parallel stores.