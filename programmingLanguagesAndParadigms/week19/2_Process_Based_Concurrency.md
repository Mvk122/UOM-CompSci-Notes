# Process Based Concurrency
* Is used when thread based concurrency is not possible eg in the case of distributed systems.
* Or when it is not wanted as implicit communication through shared memory makes it hard to reason about correctness.
* Thus communication is done through messages wherein everything between 2 messages is effectively atomic.
* Messages can be transferred in many ways: 
	* Shared memory objects
	* Network/UNIX sockets
* However it can be slower than process based concurrency.

## Messaging Types
### Remote Procedure Calls
* The sender waits for the receiver to reply.
* Easy to reason about but has very little concurrency.
### Synchronous Messaging
* The sender waits for the receiver to get the message.
* Easy to reason about but there is a lot of communication overhead.
* The sending and replying is atomic but state may have changed between them.
### Asynchronous Communication
* The sender does not wait for anything and continues the computation immediately.
* Very concurrent but hard to reason about.
* There is no guarantee the message will be received.
* Buffers are needed to manage the messages.

