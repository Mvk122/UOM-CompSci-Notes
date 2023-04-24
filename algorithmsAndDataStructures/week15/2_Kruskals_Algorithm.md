# Kruskal's Minimum Spanning Tree Algorithm
## Definition: 
* #rank: A rank in a tree is the number of edges in the longest path from a leaf to a root in a tree.
* #disjointSet: A group of sets where any given value only exists in one of the sets.

## Kruskal Steps
* Uses disjoint sets to quickly create a minimum spanning tree.
* The steps are as follows: 
	1. Create an empty set of edges that serves as the `result set`. 
	2. Convert all nodes into a set containing only that specific node.
	3. Looping over the edges ordered by weight in ascending order, if the nodes of each edge are in different sets, then: 
		1. Add the edge to the `result set`.
		2. Union the sets that contain each node. The union is done wherein the set with the smaller rank has its root point to the root of the set with the larger rank.
	4. Return the `result set`.