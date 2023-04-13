# Replica Management
![[Pasted image 20230413111058.png]]
* Replicas of data should ideally be placed in a locations with the lowest "cost" of accessing each site from other sites.
* A greedy heuristic can be used to find the optimal location to host replicas:
* ![[Pasted image 20230413111517.png]]
	1. Find the total cost of accessing each site from every other site.
	2. To find other sites, remove the first selected node and repeat to find another node.
	3. A better approach to step 2 however, is to calculate costs using $min(value, valueToFirstSelectedNode)$