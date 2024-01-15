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
* 