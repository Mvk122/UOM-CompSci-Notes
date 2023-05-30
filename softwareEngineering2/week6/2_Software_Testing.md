# Software Testing
![[Pasted image 20230530014901.png]]
* A process by which software quality and functionality can be assessed.
* Comprises of: 
	* `Validation`: Has the right software been built to the requirements of the user.
	* `Verification`: Has the software been built properly without defects or failures.
* Not everything in software can be tested hence it is better to test:
	* Ranges
	* Important conditions 
	* Edge cases
* Testing should be done at different levels:
	1. `Unit Tests`: Testing individual parts of the software and allows for agile testing as it covers a smaller scope. Furthermore it can be used as a form of documentation. However it is hard to test non-deterministic tests or tests with a large surface.
	2. `Integration Tests`: Testing the interactions between multiple components.
	3. `System Tests`: Ensuring that systems work from end to end. This can be in terms of functionality but also in terms of scalability.
	4. `Acceptance Tests`: Testing from the user's perspective.
	5. `Regression Tests`: Testing during development to ensure no new bugs have been introduced.

## White Box vs Black Box Testing
* White box testing allows for testing the internal functions and structures.
* Black box testing tests the system without knowledge of the internals, hence testing through the available interfaces of the software.