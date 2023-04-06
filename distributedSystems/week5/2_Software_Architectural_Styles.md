# Software Architectural Styles
* Refers to how:
	* Components are connected to each other.
	* Data exchanged between components.
	* How the elements are configured into a system.

## Layered Architectural Style
![[Pasted image 20230406211913.png]]
* Components are in a layered style where components higher in the stack make requests to lower layers and generally expect a response.
* The layers on the bottom provide a service to the layers on top, hence they do not make requests to higher layers on their own and calls follow a predefined path.

## Object Based Architectural Style
![[Pasted image 20230406212106.png]]
* Each object corresponds to a component which naturally encapsulates data and the operations that can be done on the data.
* Communication is done via method invocations known as `Remote Procedure Calls (RPC)`

## Resource Centered Architectural Style
![[Pasted image 20230406212338.png]]
* A central data repository made out of a distributed system is used to store a huge collection of resources that are managed individually by components.
* Resources may be added, removed, retrieved or modified by the remote application.

## Event Based Architectural Style
![[Pasted image 20230406213703.png]]
* Like a pub-sub architecture wherein processes do not explicitly know any other processes and are only able to publish notifications and subscribe to notification feeds. 
* For coordination to take place, processes need to be running at the same time.