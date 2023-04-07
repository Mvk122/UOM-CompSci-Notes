# Inter-Process Communication
* Refers to the ways that processes on different machines can exchange information.
* Processes running on different machines need to rely on message-based communication as opposed to sharing memory.

## Remote Procedure Calls
* It is based on the idea that programs should be able to call procedures located on other machines.
* It abstracts away the intricacies of message passing.
* RPC calls can be either `synchronous` or `asynchronous`:
	* `Synchronous`: After calling send, the client calls receive, thus it is blocked until the reply comes back.
	* `Asynchronous`: In the case that no reply is required, the server sends an acknowledgement as soon as a request is received and only then calls the process the client requested. The acknowledgement is used to let the client know that the server has received the message.'

## How RPC Works 
* RPC works using stubs that pack parameters into messages and messages into parameters.
* The messages can then be sent over the network.
* Hence when a message is sent:
	* the client calls the client stub which calls the OS to send it to the receiver. 
	* The receiver's OS passes the message to the receiver's stub which unpacks it. 
	* The above procedure happens again in reverse when the server sends the response to the client.

## Parameter Passing in RPC
### Parameter Marshalling
* Parameter marshalling is required as the recipient machine only receives a series of bytes with no context.
* Hence marshalling is required to transform the data into a machine and network independent format before transferring the data.

### Passing by Reference
* Pointers cannot be passed to the server as an object's memory address is specific to the address space of the machine it is running from.
* Hence when creating a request, the client has to make a copy to send the message hence passing by value instead of reference.
* However, since the server knows the client knows of the object, the server can send only the changes that need to occur on the object instead of sending the entire object back as a response.

