# Dijkstra's Algorithm
#DijkstrasAlgorithm
* Is used to find the shortest path from a source to a destination with a lower time complexity than  #BellmanFordsAlgorithm
* Unlike Bellman Ford's however, it cannot be used in a graph with negative weights.

## Shortest Path with Dijkstra's Algorithm
1. Maintain a `Priority Queue` and a `List`, starting empty where the elements of both are:
	1. The node in question. 
	2. The lowest cost to get to this node. 
	3. The predecessor of this node which lead to this current cost.
2. The priority queue is sorted by the lowest cost.
3. Add the source node to the start of the priority queue with no predecessor and cost 0.
4. For each element in the priority queue: 
	1. Add its children to the priority queue, with the given element as its predecessor and the cost being the cost to get to the element plus the cost to get to the child from the element.
		* In the case that the child already exists in the priority queue, if the cost to get to it from this element is lower than the existing one in the priority queue, replace it with this entry.
		* If the cost is higher, do nothing with this entry (don't add to priority queue).
5. Add the element to the list, which serves as a "Finished" list.
7. Once the priority queue is empty, the finished list contains the best cost to get to each node and by chaining the use of the predecessors, we can build the shortest path.

## Time Complexity of Dijkstra's Algorithm
* Since a node's value can decrease, the priority queue should be implemented with a min heap [[1_binary_heap]].
* This implementation saves time and memory by adding nodes as they are discovered, thus unreachable nodes won't be involved in the calculation. 
* Since each edge is relaxed at most once and each node is added and removed from the queue at most once, the time complexity is $O((|E| + |V| )log(|V|))$
	* Cost of relaxing, addition and extraction from the min heap: $O(log(|V|))$