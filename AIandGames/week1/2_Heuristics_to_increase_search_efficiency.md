> This lecture is similar to week 14 of Algorithms [[1_Dijkstra's_Algorithm]]
# Heuristics To Increase Search Efficiency

## Definitions
* `Heuristic`: A rule which is applied because they are found to have generally worked through trial and error.
* `Uninformed Algorithm`: An algorithm that does not take into account any state or search information other than how to traverse the tree. 

## Dijkrastra's Algorithm
* An `uninformed` algorithm to find the shortest path from a source node to a destination node in a graph.
* Explained in [[1_Dijkstra's_Algorithm]]

## Greedy Heuristic Search
* Always move to the unvisited available state nearest to the goal according to the heuristic.
* Algorithm properties:
	* Not complete
	* Will not necessarily find the optimal path 
	* Informed search
	* Can be very fast
	* Can be made complete with backtracking

## A* Search
* A combination of Dijkrastra and greedy heuristic search that is complete and informed.
* Explained here: [[2_A_Star_Search]]

## Using Search in Games
* A* Search cannot be used in games, however modifications can be made to it to take into account the behavior of other players to form a good strategy.
* Furthermore, the heuristic would instead be a `board evaluation function`