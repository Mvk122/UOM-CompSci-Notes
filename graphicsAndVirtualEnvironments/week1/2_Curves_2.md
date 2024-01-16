# Velocity
![[Pasted image 20240116170958.png]]
* The velocity is also known as the tangent to the curve at a given point.
* The differential term can be calculated by differentiating the equation of the bezier curve.

# Curvature (Acceleration)
![[Pasted image 20240116171422.png]]
* Can be calculated the same as velocity, except it is using the second derivative.

# Orders of Continuity
![[Pasted image 20240116171637.png]]
## C0
* The curves connect but there can be a sharp kick/corner at the boundary
## G1
* The tangents at the connection are pointing in the same direction.
## C1
* The tangent at the connection are exactly the same
## C2
* The tangent and also the derivative of the tangent are exactly the same at the connection

# B-Spline Curves
![[Pasted image 20240116171801.png]]
* Cubic.
* Uses 4 control points.
* Are locally cubic (each segment of the curve is cubic).
* They are not constrained to passing through any of the control points.
* Is bounded by a convex hull, like bezier curves.
* The sum of its bernstein polynomials is always 1.
![[Pasted image 20240116171935.png]]
* Equation of a b-spline curve.

# Converting Between Bezier and B-Spline Curves
* Consider how a Curve is represented:
$$
P = Geometry * Spline Basis * Power Basis 
$$
* Allow $B_1$ to be the basis for bezier and $B_2$ to be the basis for B-Spline. 
$$
P(t) = G_1B_1T_1(t)
$$
* We can multiply by $B_2^{-1}B_2$ and it won't make a change as that is the unity matrix.
$$
P(t) = G_1B_1B_2^{-1}B_2T_1(t)
$$
* Now, allow for $G_1B_1B_2^{-1}$ to be the new $Geometry$ and $B_2$ Becomes the new basis.
* Thus the basis is now the b-spline basis and we have the new control points (Geometry) for representing the originally bezier curve as a b-spline.

# Non-Uniform Rational Basis Spline
![[Pasted image 20240116172911.png]]
* Each control point has a weight that it contributes to the curve.
* The curve is defined by the ratio of the cubic terms.
* They are more flexible than b-spline and bezier curves, hence are used more in computer design than the latter.
* (No need to know how to derive them).