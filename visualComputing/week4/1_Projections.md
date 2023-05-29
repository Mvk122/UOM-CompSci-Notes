* Projections are a means to display a 3D object on a 2D plane in a manner that balances the need for: 
	* Accurate size 
	* Accurate shape 
	* Accurate angles

## Parallel Projection
![[Pasted image 20230529002034.png]]
* Appears as if light coming form infinity intersect the object in parallel.
* An example is `Orthographic` projection wherein the viewpoint is from a particular 2D plane such that the object can be viewed at that angle (either the front, side or top). This means: 
	* There is no distortion of angles or lengths. 
	* However only 2 out of 3 of the planes are visible at once.
* For example, if we are viewing from a plane of Z=0, the only transformation that needs to happen is that: 
	* $x_p = x$
	* $y_p = y$
	* $z = 0$
* The matrix transformation is as shows: 
![[Pasted image 20230529002621.png]]
* There is a loss of information however as this matrix is `singular` (not reversible).
* There are other parallel projections that all also point towards the origin: 
	* `Isometric`: The plane is at 45 degrees to all axes 
	* `Dimetric`: The projection plane is symmetrical to 2 of (X,Y,Z)
	* `Trimetric`: The projection plane is placed arbitrarily.

## Perspective Projection 
![[Pasted image 20230529003823.png]]
* Rays of light pass from the object, through the projection plane and converge at a point on the centre of projection.
* Hence the following occur:
	* Objects further away from the projection plane appear smaller. 
	* Parallel lines appear to converge in the distance.
* The matrix transformation for a perspective transformation is: 
![[Pasted image 20230529014151.png]]
* A problem with perspective projection is that we have lost the z coordinate by setting it to d.
* This is an issue as we want to keep that information to do hidden-surface removal.
* A solution is `projection normalisation` wherein a transformation `PN` can be done with the perspective transformation to create an orthographic projection that preserves the depth information
![[Pasted image 20230529021210.png]]

## View Volumes
* Refers to the camera's field of view wherein only items within the view volume can be seen by the camera at the current time.

## Clipping 
* Removes objects outside of the view volume