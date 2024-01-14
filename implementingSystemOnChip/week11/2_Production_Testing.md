# Production Testing 
* Not every manufactured chip will work, production testing runs tests on manufactured chips to test that they work.
### Differences with Testing the Source
* Testing is done on physical chips instead of on simulations.
### Challenges with Production Testing
#### Automatic Test Pattern Generation 
* There are too many different paths through the logic to create tests that test that every component in the chip physically works, hence ATPG is used to generate the tests.
* This can be difficult as: 
	* Power constraints mean that it is infeasible to test multiple blocks simultaneously.
	* Testing needs to be done through multiple layers of logic hence there is a loss in `controllability` as compared to testing in software. This can also mean that more cycles are needed to test something.
	*  The outputs need to be checked for incorrectness and this can be hard as there can be blocks of logic in between the output and feedback to the user, hence there is a loss in `observability` as compared to testing in software.
## Built In Self Test
* A chip being able to test itself through the generation of test patterns using a ROM or a psuedo-random number generator.
* The output signature can be collected as an output `cyclic redundancy checks`.
* Modern SoCs will have one or more processors on board which can be exploited for test purposes and thus self test software can either: 
	* Be built into a boot ROM. 
	* Downloaded into RAM from a test port.
* Using an existing processor has several advantages:
	* The ROMs size will be known in advance but its contents can be fixed late during the process. 
	* Since the ROM programming is done with a single metal layer, it is cheap to change later. 
	* If downloading from a tester, it is possible to develop the tests after the chips are in fabrication though this comes with an added stage for downloading.

## Scan Chains
![[Pasted image 20240114170547.png]]
* Wires connected to buried logic blocks to achieve controllability and observability.
* Flip flops as part of the scan chain are placed the normal way but late in the process are replaced with scan flip flops with the following properties:
	* They are connected to the previous flip flop in the scan chain. 
	* They are connected to a global input which decides if their input should be from their combinatorial logic or from the previous scan flip flop.
* Hence the scan chain is essentially a massive shift register.
## Boundary Scans