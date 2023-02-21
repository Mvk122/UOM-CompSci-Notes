## Tessellation
![[Pasted image 20230221142827.png]]
* Is a technique for converting concave polygons into convex polygons to allow them to be rendered properly.

## Back Face Culling
* Back face culling is used to skip rendering polygons that are blocked by other polygons.
* Back face culling uses the `surface normal`, which is the vector perpendicular to the polygon to decide whether the polygon is in frame.

## Calculating the Surface Normal
* Choose a pair of sequential edges $E_1$ and $E_2$ and compute their vectors.
* Inverse $E_1$ so both vectors emanate from the same point.
* Use the cross product $N = E_2 \times E_1$ to get the surface normal.
* Usually N is normalised in the process.