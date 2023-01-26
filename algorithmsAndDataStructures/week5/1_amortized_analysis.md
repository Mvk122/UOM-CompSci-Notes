# Amortized Analysis

* Averaging the time required to perform a sequence of data structure operations over all the operations performed.
* Not the same as `average case analysis` as probability is not involved.

## Dynamic Tables
* Tables that increase in size, allocating a new larger table when it overflows.
* The goal is to make a table that is as small as possible but large enough so that it won't overflow.
* The time complexity of this structure is `Θ(1)` per insertion even though the reallocation takes `Θ(n)` as it is amortized over `n` times where the reallocation did not take place during inserts.
