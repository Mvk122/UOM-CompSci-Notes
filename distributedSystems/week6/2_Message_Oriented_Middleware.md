# Message Oriented Middleware

* Is a message queue that allows for the client and server to not have to be online at the same time.
* It is used when message transfers are allowed to take minutes instead of milliseconds.
* Multiple queues can be chained.
* Messages are sent to the queue by the client, the response it receives is that the queue has received the message.
* When the server comes online, it can request the messages from the queue.
* Since the server will not have received the message by the time a response is generated to the client, the client is only guaranteed that the message will eventually be inserted into the recipient's queue.