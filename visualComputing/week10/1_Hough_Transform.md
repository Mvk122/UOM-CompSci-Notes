# Hough Transform

## Hough Lines
* Used to check if a set of points constitutes a line.
1. Given the equation of a line is $y = mx + c$, we can rearrange it to $c = -xm + y$ so that we can vary the value of m to calculate c.
2. Then for each point, we can substitute their (x, y) coordinates into the equation
	* Eg (10, -10) would become c = -10m - 10
	* We doe this as c = -10m - 10 in hough space represents every possible line through (-10, 10)
3. We can then plot the graph as such 
![[Pasted image 20230602020626.png]]
4. As shown in the graph, 3 lines converge on m = -1, c=0 hence the equation of the line that goes through 3 of the points is $y  = -1x + 0$.
5. To calculate this programmatically, use a 2d array which has a list of potential values for c and m:
![[Pasted image 20230602020826.png]]
6. Entries are incremented for each point and the entries with the highest values can be chosen.

## Hough Lines with Polar Coordinates
![[Pasted image 20230602021205.png]]
* The cartesian method of doing hough lines can be problematic for vertical lines as that would constitute a value of `infinity` for m.
1. The process is the same, where x and y are substituted to get a value for r and theta
![[Pasted image 20230602021611.png]]
