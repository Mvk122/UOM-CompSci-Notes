# 1a
## i
The existence of an x value could mean that an error is present hence helps in debugging 
## ii
The value means don't care hence the synthesizer can implement the logic with less components

# 1b
* If the signal is not a clock and is not synchronous to the clock, it may change when the value is being sampled, leading to metastability issues. This can lead to glitching.
* The signal may switch faster than the clock hence latches and other components that are too slow may lead to timing issues.

## 1c
* Using a systolic array as the cycles can be very fast due to not having to wait for carry propogation. This also allows for the throughput to be very fast as there is one result every fast cycle.

## 1d
* By using random patterns, we can quickly generate tests that yield a high code coverage.
* Advantage: Very fast to produce and can give a very high test coverage.
* Disadvantage: May not cover all input cases and paths.

## 1e
* Can detect: 
	* Whether or not all possible code paths have been taken.
	* Whether or not the output matches with the golden data
* Cannot detect: 
	* Whether or not it does what the designer intended, not what the designer implemented.
	* Timing issues

## 1f
* Faster switching, allowing for a faster clock speed.
* Higher power usage from short circuit (dynamic) switching.

## 1g
* Less switching per unit time, hence:
	* a lower amount of power lost from short circuit.
	* A lower amount of power lost from switching.
* More time is spent hence more static power loss from leakage as the processor takes more time.

## 1h
* Small amount of current that flows even when it should be in the off state due to physical imperfections.

## 1i
* This allows for less wiring to be used as opposed to parallel
	* USB 
	* Ethernet

## 1j
* Buffer insertion 