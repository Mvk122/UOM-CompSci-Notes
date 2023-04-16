# Topological Sorting
* An arrangement wherein nodes are placed sequentially (all edges point forward).
* This can be used in the scenario of a build system wherein connections correspond to dependencies and dependencies need to be built before the node.
* A topological sort is possible if there are no cycles (`Directed Acyclic Graph` ).

## Cycle Detection and Topological Sort with DFS
* Nodes will have one of 3 stages:
	* `Open`: When the node is first encountered. 
	* `Done`: All the node's children have been discovered. 
	* `New`: The default state.
* The algorithm goes as follows:
	* Run a DFS on a node, marking it as open.
	* When exploring the children, mark them as open too.
	* If an open node is discovered, there is a cycle, so abort the function.
	* If a node has no children, mark it as done.
* To create a topological sort, create a list and prepend nodes that become done to the list. This becomes the topologically sorted list.