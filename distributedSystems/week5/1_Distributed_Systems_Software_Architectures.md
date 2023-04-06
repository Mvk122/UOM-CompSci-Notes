# Distributed Systems Software Architectures

## Centralised Architectures
![[Pasted image 20230406211043.png]]
* Traditional client-server architectures wherein a single server implements most of the software components and remote clients can access the server using simple communication means.
* Is usually implemented using a `request-reply` behaviour.
* Typically, the server also has to act like a client eg in the case of accessing a database to gain information to respond to client requests, breaking the architecture up into 3 distinct logical layers. Thus it is usually broken up into:
	* The user interface layer (client)
	* Processing Layer (server)
	* Data Layer (server)

## Decentralised Architectures
* Peer-to-peer type architectures in which all nodes play equal roles.

## Hybrid Architectures
* Combining elements from centralised and decentralised architectures.