# Fault Tolerance
* Fault tolerance is associated with the following dependability requirements:
	* `Availability`: The probability that the system is operating correctly at any given moment.
	* `Reliability`: The length of time that a system runs continually without failure.
	* `Safety`: If and when failures occur, the consequences are not catastrophic for the system.
	* `Maintainability`: How easily a failed system can be repaired.

## Fault Tolerant Systems
* A system that can provide its service even in the presence of faults.
	* Eg in the case of applying error correcting codes to mitigate the effects of faulty transmission lines.

## Types of Failures
* `Crash Failures`: Halts but works correctly until it halts. 
* `Omission Failure`: Failure to respond to incoming messages
* `Timing Failure`: Responses lie outside a specified time interval.
* `Response Failure`: Response is incorrect.
* `Arbitrary Failures`: Responses are arbitrary and can occur at any time. This is the most serious type of failure as it can produce outputs that cannot be detected as incorrect but are.

