# Compiler Backend
![[Pasted image 20230406054521.png]]
## Intermediate Code Optimisation
* The intermediate code can be optimised to remove duplication among other optimisations to reduce the amount of instructions needed/memory calls. This is usually called the `middle end` of the compiler.

## Code Generation
* Mapping the Abstract Syntax Tree into a linear list of target machine instructions in a symbolic form.
* This is usually done in more than polynomial time as the following optimisations take place:
	* `Instruction Selection`: IR code needs to be pattern matched into instructions that can usually do more than one operation at a time.
	* `Register Allocation`: Each value should be in a register when it is used, the right allocation of registers is required to prevent constant switching of memory between main memory and registers.
	* `Instruction Scheduling`: Rearranging of instructions to take advantage of multiple function units.
