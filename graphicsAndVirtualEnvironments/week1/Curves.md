# Definitions
![[Pasted image 20240116113159.png]]
* `Polylines`: A sequence of vertices connected by straight line segments.
* `Spline`: A curve that connects 2 or more points.

# Ways of Representing Geometry
## Explicit
* Representations like point clouds and polygon meshes which are easy to work with and provide precise control over the shape of objects.
## Implicit
* Representations like algebraic surfaces and level sets which are more simple and efficient.


# Ways of Constructing Curves
![[Pasted image 20240116113527.png]]
* `Interpolation`: The curve passes through all control points.
* `Approximation`: The curve generally approximates its way around the points, allowing us to use fewer control points, giving us more flexibility and allowing for the simplification of more complex curves.

# Cubic Bezier Curve
![[Pasted image 20240116113717.png]]
* The curve is always within the bounding box of the control points.
	* This is because the sum of the bernstein polynomials is always less than 1.
* P1 and P4 are always tangent to the curve.
![[Pasted image 20240116170212.png]]
* The equation of the curve is derived from 4 bernstein polynomials.
![[Pasted image 20240116170304.png]]
* It can also be represented in a matrix form.
![[Pasted image 20240116170631.png]]
* The bernstein function coefficients can be found for any polyn