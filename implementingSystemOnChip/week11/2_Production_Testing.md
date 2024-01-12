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


## Scan Chains
* Wires connected to buried logic blocks to achieve controllability and observability

## Boundary Scans