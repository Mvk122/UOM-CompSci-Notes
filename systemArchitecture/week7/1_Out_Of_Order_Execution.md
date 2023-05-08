# Out of Order Execution
#outOfOrderExecution
## Instruction Reordering
* Reordering instructions is done to make use of parallelism in superscalar processors by avoiding data dependencies. It can be done either by the compiler or by hardware on the chip.
### Compiler Instruction Reordering
* If the compiler can be relied on for instruction reordering, expensive checking logic can be eliminated from the processor.
* This is usually done using `VLIW` (Very Long Instruction Words) for the compiler to state which instructions can be run in parallel.
* The compiler will be able to use `NOPs` if necessary.
* There are many downsides however: 
	* Binaries created by compilers targeting specific hardware would tie the optimum code to that specific piece of hardware.
	* There could be `code bloat` in VLIW with excessive NOPs.

### Reordering in Hardware
* Reordering is usually done in hardware, however it requires the following additional hardware to operate: 
	* `Instruction Buffer`: To store all issued instructions.
	* `Dynamic Scheduler`: To send non-conflicted instructions to execute. 
	* `Deferred memory and register access`: Hardware needs to be created to allow these to be able to be delayed until older instructions are finished to comply with application semantics.