# Graphs 
![[Pasted image 20230416152442.png]]
* A graph is a set of nodes that have a set of connections. It can be one of either:
	* `Directed`: The edges represent pointing eg 1 points to 2 does not mean 2 points to 1.
	* `Undirected`: The edges represent connections hence 1 points to 2 means 2 also points to 1.
* There are no parallel edges (2 edges with the same origin and destination).
* There are no loops (nodes pointing to themselves).

## Graph Operations
* `Empty`: Creates an empty graph
* `AddEdge(u,v)`: Add an edge between u and v
* `RemoveEdge(u,v)`: Remove an edge between u and v
* `IsEdge(u,v)`: Is there an edge between u and v
* `Successor(u)`: What edges are coming out of u

## Graph Implementations
* An adjacency list is preferred when the density (number of connections compared to the number of nodes) is low, an adjacency matrix is preferred otherwise.
### Adjacency Lists 
* Each node has a list of edges that it is connected to. This is a list.
* There is a list with the above list for all the nodes:
```python
# 1 is connected to 2, 3 and 2 is connected to 3 
adjacency_list = [[1, 2, 3], [2,3], [3]]
```
* Time complexities:
	* `AddEdge`: $O(1)$
	* `RemoveEdge`: $O(|V|)$ as the vertex needs to be searched for
	* `IsEdge`: $O(|V|)$ as the vertex needs to be searched for
	* `Successor`: $O(1)$
* Memory Complexity: $O(|V| + |E|)$

### Adjacency Matrices
![[Pasted image 20230416153747.png]]
* 2D array with a Boolean representing if there is an edge between 2 of the nodes.
* Memory Complexity: $O(|V|^2)$
* Time Complexities:
	* `AddEdge`: $O(1)$
	* `RemoveEdge`: $O(1)$
	* `IsEdge`: $O(1)$
	* `Successor`: $O(|V|)$
