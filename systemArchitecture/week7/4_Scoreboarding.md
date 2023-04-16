# Out of Order Execution with Scoreboarding
## Scoreboard
![[Pasted image 20230414074038.png]]
* The `scoreboard` is a centralized hardware mechanism which dynamically constructs the dependency graph for a window of instructions to allow for instructions to be processed as soon as their operands are available and there are no hazard conditions.
* This allows for out-of-order execution.
* It has 2 operations that allow for instructions to execute when both operations hold: 
	* `Issue`: decoding instructions and checking for structural hazards. 
	* `Read operands`: Wait until there are no data hazards then read the operands.
* Generally scoreboards use `In-order issuing` and `out-of-order execution`.

## Information Stored in the Scoreboard
* The scoreboard has 3 tables: 
	* `Instruction Status`: Contains the status of each instruction.
	* `Functional Unit Status`: Contains the status of each functional unit
	* `Register result Status`: Indicates which functional unit will write each register.

### Instruction Status Table
* Contains which of the 4 stages the given instruction is in, either: 
	* `ID`: Instruction decode
	* `RD`: Read Operands
	* `EX`: Operate on operands
	* `WB`: Write results
### Functional Unit Status Table
* Status if the functional unit that the instruction is in, either: 
	* `Busy`: Whether the unit is being used or not.
	* `Op`: The operation being performed in the unit
	* `Fi`: The destination register
	* `Fj, Fk`: Source register numbers
	* `Ql, Qk`: The functional units producing the source registers `Fj, Fk`
	* `Rj, Rk`: Flags indicating when `Fj, Fk` are ready, it is set to yes when each operand is read.
### Register Result Status
* Indicates for each register, which functional unit will write to it.

## Stages of a Scoreboard Pipeline
![[Pasted image 20230414084242.png]]
### Issue (ID)
* Decodes instructions and checks for `Write after Write` hazards wherein no other active instruction has the same destination register.
* If a suitable functional unit is free, the instruction is issued to it and the FU status table is updated.
### Read Operands (RD)
* Waits until there are no `Read after Write` hazards wherein a source operand is not available as a currently active instruction is going to write to it.
* Once all operands are available, the scoreboard tells the FU to proceed to execution.
### Execution (EX)
* Functional Unit operates on operands, when the result is ready, the scoreboard is notified.
### Write Result (WB)
* Waits until there are no `Write after Read` hazards wherein the register to be written to first needs to have its current result be read by a previous instruction.

## Limitations of Scoreboards
* They are not too scalable as they scale more than linearly with the number of score entries and the number and types of functional units.