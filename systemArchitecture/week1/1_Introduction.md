## Moore's Law
* A prediction that the number of components on an integrated circuit will double every 18 months.
* Done usually by reducing the size of components in a chip with the following consequences:
	* More components per chip as each component is smaller and the chip size can remain constant.
	* Faster processing either by increased clock speed or increased parallelism
	* Lower energy consumption per component as the resistance through each component decreases due to their smaller size.

## Dennard Scaling
* In general, the power consumption of chips has stayed roughly constant despite speed increases due to real world constraints.
* In portable equipment, lower power requirements are prioritised to increase battery life.
* In tethered equipment, cooling will become an issue if power consumption increases.

# Introduction

* The main performance impacting components of the processor are the `processor`, `memory` and `I/O`
* There is a memory wall wherein the size of new memory is increasing at a rapid rate but the increase in memory speed is slow. Memory speed is defined in 2 ways:
	* `Latency`: The time taken to complete a memory operation.
	* `Bandwidth`: The rate at which data can be moved.

## Amdahl's Second Law
* A balanced computer should have 1MIPS processing per 1MB memory per 1Mb/s I/O