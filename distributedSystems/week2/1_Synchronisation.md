* Synchronisation requires fast and reliable communication between processes.

## Synchronisation Definitions
* `Data Synchronisation`: Keeping multiple copies of a dataset in coherence with one another given that the copies of the data are located in different nodes.
* `Process Synchronisation`: Multiple processes needing to act together to achieve a certain overall purpose.

## Why is Synchronisation required
* When processes need to agree on an ordering of events.
* When processes need to simultaneously access shared resources that are mutually exclusive to prevent deadlock. [[operatingSystems/content/week6]]

## Challenges with Synchronisation
* Networks are unreliable hence messages can take a variable amount of time to arrive or may not arrive at all.
* Timestamps are not an adequate solution as they do not take into account the amount of time taken for the timestamp message to reach the recipient.
* The only guarantee that can be made is that a message will not arrive at a destination before it was sent.

## Messaging Ordering Principles
* If a and b occur in the same process and a occurs before b then `a->b`.
* If a is the event of a message being sent and b is the event of the message being received by another process then `a->b`.
* If `a->b` and `b->c` then `a->c`.
* If 2 events happen in different processes without an exchange of messages then `x->y` and `y->x` are both untrue.

## Logical Clocks
* Logical clocks provide a distributed incremental pseudo time to events in a distributed system.
	* It allows for a partial ordering of events in a system.

### Lamport's Logical Clock
* All processors contain a logical clock of integers starting at 0.
* When an event occurs on a processor, increment its clock by 1.
* When a processor sends a message to another, attach the processor's logical clock.
* Let the recipient be LCy and the message it received be LCx, then:
```python
	if LCy < (LCx + 1):
		LCy = LCx + 1
```
* Thus if `a->b` then `LCa < LCb`. However `LCa < LCb` does not imply `a->b`.
