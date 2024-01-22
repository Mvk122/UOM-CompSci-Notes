# Monte Carlo Stages 
## Selection 
* Starting at the root node, at every iteration, child selection is recursively done to traverse the game tree looking for the most important and expandable node.
* A node is expandable if it is:
	* Non-terminal
	* Has unvisited children
### Selection Methods (UCT)
* `UCT` is the preferred selection method which chooses:
	* Unselected children, where children which have been selected less often are chosen if they have the same value as other children.
* `UCT` works as children with lower true values will be chosen less often and the best child will be chosen exponentially more often.
* Each node stores:
	* $Q(v)$ : The sum of all payoffs that passed through this node. 
	* $N(v)$ : The count of the number of times it has been visited. 
* Thus the estimated value of the node is $Q(v)/N(v)$.
![[Pasted image 20240122084438.png]]
* The second part of the equation is the exploration constant.
* $
## Expansion 
* Increase the size of the partial tree by expanding nodes (usually just 1 node). 
## Play Out 
* Run a simulation on the expanded nodes by doing random self play.
## Back Up
* The statistics of the added node and its ancestors are backed up.