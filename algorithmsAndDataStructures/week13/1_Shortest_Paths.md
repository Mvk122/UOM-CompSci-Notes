# Shortest Paths

## Definitions
![[Pasted image 20230422181429.png]]
* `Negative Weight Cycle`: A cycle in a graph where the summation of weights is negative.

## Shortest Paths with BFS
* Using a `predecessor map` and a `FIFO Queue`, we can use BFS to get the shortest path from a source to a destination.
	* Shortest path in this definition is the path that uses the fewest amount of edges.
* The steps are as follows: 
	1. Start at the destination node.
	2. Mark it as discovered and add all its undiscovered children to the FIFO Queue.
	3. Add the destination node (their parent) as their predecessor in the predecessor map for each of the children.
	4. Take the first element out of the queue, mark it as discovered and repeat from step 2 to 4.
	5. When the source node is found, follow the predecessor map back to the destination to get the shortest path.

## Shortest Paths in a Weighted Graph (Bellman Ford)
* Uses the concept of overestimations and refining estimations to get the best path from a source to a destination.
* The steps are as follows: 
	1. Create a table with every node and a corresponding `Best Cost From Source` for each node, with a starting value of infinity. (The source city can have a cost of 0)
	2. For each node in the graph, get the value of the distance from the source to the children of the node in question. (Eg to get from Node 1 to 2 is cost `a` and from Node 2 to Node 3 is cost `b` hence the cost from Node 1 to Node 3 through this path is `a + b`).
	3. If this cost is better than the current value in the table for the traversal from the source to the child, replace the value in the table with this new value.
	4. Once step 1 to 3 is done for each of the nodes, do another round, using the table to check if there is a better cost, repeat this step until there is a round with no further changes.
		1. Repeat up to a maximum of $|V|$ times as if more iterations are required, a `negative weight cycle` exists, hence there is no solution to the problem.
* The time complexity is as follows: 
	* The worst case has $|V|$ rounds where V is the amount of vertices in the graph. 
	* Each round inspects $|E|$ edges where E is the amount of edges in the graph.
	* The time complexity to relax an edge is $O(1)$.
	* Hence the worst case is $O(|V| |E|)$