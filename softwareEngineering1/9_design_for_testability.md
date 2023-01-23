# Design for Testability

## What stops code from being testable
* Non-deterministic code
* Hard coding/hiding behaviour inappropriately
* Not allowing inheritance/overriding
    * Static code
    * Constructors
* Complex/slow configuration requirements
* Tell don't ask 

## Test Doubles
* The behaviour of classes that the class under test works with needs to be controlled.
* Thus a `test double` is a version of a production code object whose behaviour is predictable/ controllable in a way that helps us write the test.


## Test Double Types
* `Dummies`: Passed around but never actually used, Often used to fill parameter lists
* `Stubs`: Provides canned answers to calls made during the test
* `Fakes`: Have working implementations but take short cuts compared to the production object
* `Mocks`: Test doubles created on the fly with behaviour that matches programmed expectations