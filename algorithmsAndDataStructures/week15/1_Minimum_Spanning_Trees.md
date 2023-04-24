# Minimum Spanning Trees
#MinimumSpanningTrees 
## Definitions 
* `Minimum Spanning Tree`: A graph where all of the nodes are connected with the sum of the weight of the edges minimised.
* `Safe Edge`: A safe edge is an edge connecting a minimum spanning tree to another node with the lowest edge weight possible without introducing any cycles. #safeEdge
* `Light Edge`: An edge crossing a cut where it is the minimum weight of an edge that crosses the cut. #lightEdge

## Graph Cuts
* A cut is a partition in a graph.
* A cut `respects` a set of edges if no edge in the set crosses the cut. 
* An edge crosses a cut if its endpoints are in different sides of the partition.

## Greedy Algorithm for a Minimum Spanning Tree
1. Start with `A`, an empty set of nodes.
2. While `A` does not form a spanning tree, find an edge that is safe for `A` and add it to `A`.
3. The loop terminates when `A` is a minimum spanning tree, executing at most $|V| -1$ times.

## Recognising Safe Edges
1. Cut the current minimum spanning tree from the rest of the graph. 
2. The `light edge` of this cut is the `safe edge` that can be added to the minimum spanning tree.