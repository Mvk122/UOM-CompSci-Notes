# A* Search
#AStarSearch
* Is a modification of #DijkstrasAlgorithm that uses an underestimating #heuristic to reduce the search space and only try solutions with a lower estimated distance.

## A* Search
* Instead of using only the cost of the path for each node, the cost to get to each node is the sum of the total cost to get there plus the underestimate of the distance to reach the solution. 
* For example, when considering journeys on a map, the heuristic could be the Euclidean distance from the node to the destination as no journey could be shorter than the straight line path from a node to the destination.

## Heuristic Admissibility Criteria
* It must never overestimate the true cost of reaching a destination.
* It must be monotone (fits the triangle inequality):
![[Pasted image 20230422191848.png]]
