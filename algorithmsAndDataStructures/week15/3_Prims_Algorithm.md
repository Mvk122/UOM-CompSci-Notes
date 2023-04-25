# Prims Minimum Spanning Tree Algorithm
#PrimsAlgorithm
* Prim's algorithm is used to create minimum spanning trees, using the concept of a priority queue like #DijkstrasAlgorithm.
* It uses a greedy approach wherein:
	1. a node is selected at random to be the root. 
	2. A cut is made between the root and the rest of the graph. 
	3. The #lightEdge  is then added to the list of edges comprising the Minimum Spanning Tree.
	4. The above is repeated until all nodes are in the minimum spanning tree. In each iteration, the node on the other side of the #lightEdge is added to the MST.

## Algorithm Implementation
1.  Create an empty `priority queue` and `list`. The list holds the nodes that comprise the current MST, the priority queue contains the nodes to be examined.
	* Each element in both contains the node, their weight, and their parent.
2. Add all the nodes to the priority queue, by default they have no parent and a weight of infinity. 
3. Pick an arbitrary node and assign it the weight of 0.
4. While the priority queue is not empty, take an element from the top and do the following:
	1. Add its children to the priority queue with the given element as its parent and its cost being the weight between the child and the parent. 
		* If it already exists in the priority queue and this cost is lower than the existing one, replace it with this entry.
		* If the cost is higher, do nothing with this entry.
5. Add the element to the finished list. By chaining the use of the parents of each element, we can build the MST.

## Time Complexity of Prim's Algorithm
* Time Complexity is $|E| + |V| log(|V|$)$