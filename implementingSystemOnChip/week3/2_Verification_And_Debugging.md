## Functional Tests
* Testing the functionality of the design, testing:
	* If the initial state is achieved. 
	* If there are no unknowns in the circuit.
	* If all statements are tested.
	* If the most straightforward operations work (unit tests).

## Things to test in Functional tests
### Control
* Do the interfaces go through the expected protocol steps.
* Are the FSMs behaving as expected, through observing the internal state. 
* Test all the transitions in the state diagram for all the reasons that may trigger them.
### Data
* Checking that the output data is correct by comparing it with independently generated test results.
* Self-testing for processors may be possible by running software on it and seeing if it crashes.

## Designing Verification Test Strategies
* `Individual tests`: Testing that at least one case of every known circumstance is used. 
	* Effective but Expensive. 
* `Algorithmically Generated`: All possible cases of inputs and regular input patterns, easy to do but requires some design effort. 
* `Random Patterns (Monte Carlo)`: 