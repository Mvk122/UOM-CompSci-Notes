# Synchronisation Algorithms

* Algorithms need to be developed to prevent events from occurring simultaneously when sharing resources.
* This needs to occur to prevent resources from being unable to complete their tasks because of a change in a resource as a result of another concurrent task eg the final ticket gets purchased by a client while another client also has it selected hence the second client is unable to purchase the ticket halfway through the process.

## Resource Control Algorithms
### Centralised Lock Server and Mutual Exclusion Lock
* Clients send a request to the lock server for a mutex on a given resource.
* When it is given the mutex, it executes its process and sends a message to the lock server announcing that it is done with the resource, allowing the lock server to pass the mutex to the next client in the queue.
* This solution has 2 limitations:
	* The lock server is a single point of failure. 
	* If any part of the sequence fails, the state of the system is not reset to the starting state.

### Two Phase Commit Algorithm
* Ensures atomicity of the process by ensuring it either succeeds or that the system is returned to its original state on failure.
* A coordinator node sends a request to all participant nodes to start the process.
* The participant nodes either send `VOTE_COMMIT` or `VOTE_ABORT` to signal if they can proceed.
* If all participants `VOTE_COMMIT`, the coordinator node sends a `GLOBAL_COMMIT` to finalise the changes.
* Otherwise it sends a `GLOBAL_ABORT` and all participant nodes roll back to their previous state.
* This solution needs another solution to decide which node becomes the `coordinator`.

## Coordinator Node Selection
### Bully Algorithm
* A node sends an `ELECTION` message to all nodes. Any nodes with a higher number will respond.
* If none respond before the timeout, then the first node (the node that sent the `ELECTION` message) is the highest node and is the coordinator. It lets other nodes know by sending a `VICTORY` message.
* If a node or multiple nodes respond, the responders then sends out their own `ELECTION` messages as they have a higher number and restarts the process. The initial node does nothing and waits for a `VICTORY` message.

## Clock Synchronisation Algorithms
* As long as some amount of error is acceptable, there are algorithms to get nodes to be nearly synchronised.

### Cristian's Algorithm
* A node requests the time from a time server.
* The time server responds with its time.
* The node sets its time to $T + RTT/2$ where T is the time from the time server and RTT is the round trip time of the request.
* This solution has 2 limitations:
	* It assumes that the send and receive time of the request are the same.
	* It relies on the node's internal clock to not drift.

### The Berkeley Algorithm
* The master polls the slaves that reply with their times. 
* The master sets its time to the average of its slaves, ignoring outliers.
* The master sends the amount that each slave must increment/decrement its time taking into account the RTT of the original message and their original times.