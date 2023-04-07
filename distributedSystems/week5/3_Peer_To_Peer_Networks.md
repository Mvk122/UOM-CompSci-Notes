# Peer To Peer Networks

* Systems in which all nodes act as both a client and a server.
* There is a `horizontal distribution` of functionality across the nodes in a peer to peer network to evenly balance the workload on each of the machines.
* Due to each node acting as both a client and a server, processes are organised into an overlay network showing each node and the nodes that it can make a direct connection to.
* Nodes are then able to communicate with any arbitrary node by passing messages between nodes.

## Structured Peer to Peer Networks
![[Pasted image 20230407184220.png]]
* In structured P2P systems, nodes are organised in an overlay that adheres to a specific deterministic topology eg in a tree/ring
* This allows for data to be easily looked up as the node that stores a specific piece of data can be deciphered through some function of the data's ID.
	* For example, in a hypercube, a hashing function could be used on the ID of a piece of data with the output being a number corresponding to a node's ID.
* This allows for efficient routing of data as any node can, through the construction of a pathway, efficiently route data between 2 nodes that aren't directly connected.

## Unstructured Peer to Peer Networks
* Each node maintains an ad-hoc list of neighbours such that the overlay resembles a random graph.
* When a node joins, it contacts a well known node for a list of peers. 
* The list can be used to find more peers and ignore others.
* The list of peers is changed almost continuously.
* Due to a lack of structure, searching for data is necessary.

## Searching through Peer to Peer Networks
### Flooding Search
* When a node needs data, it issues a request to all its neighbours.
* If the neighbour does not have the data and has not seen the request before, it will forward the request to all its neighbours.
* If a neighbour has the data it can either:
	* Send the data to the node that forwarded the request, which then forwards it in a chain that reaches the original.
	* Send the data straight back to the issuer.
* Flooding is expensive hence requests often have an attached `Time To Live (TTL)` stating the maximum number of times a request is allowed to be forwarded.


### Random Walk Search
* The same as the flooding search except data is only forwarded to a random neighbour instead of all of them.
* It is less network intensive but it takes a longer time to get a result. Thus the issuer can start many random walks at once.
* TTL still applies, however another strategy is to check with the original issuer if it still needs the data, to check if another random walk has already yielded an answer.

## Improving Search in Unstructured Networks
* To improve scalability, systems can use special index nodes that maintain an index of data items that can be the first point of contact when searching for data.
* This technique is used in `Content Delivery Networks (CDNs)`