# Definitions
* `Edge`: An edge is an extended, significant local change in image intensity.

## Better Edge Detection
* Edge detection can be improved by using an algorithm that uses the direction as well as magnitude of the edges.
* We can do this by taking 2 values:
	* The horizontal gradient by subtracting the pixel value from the value of the pixel on its right.
	* The vertical gradient by subtracting the pixel value from the pixel below it.
* Then calculate the magnitude with $\sqrt{dx^2 + dy^2}$
* Then calculate the direction of the gradient vector with $tan^{-1}(\frac{dy}{dx})$
* The directions are normals to the edges themselves. Thus the edges can be drawn using the direction and magnitudes. 

## Roberts Cross Edge Detector
![[Pasted image 20230601040355.png]]
* The edges can't be stored in the same image because there is no centre pixel (awkward edge localisation)
* This is very noise sensitive as if 1 pixel is corrupted, the edge strength is equally corrupted.

## Prewitt Operator
![[Pasted image 20230601040526.png]]
* More complex than roberts cross edge detector but it is more robust against noise.
* This is because it separates into an averaging filter that smooths along the rows. (the first matrix after the = is an average matrix)
![[Pasted image 20230601040746.png]]
* Also creates thicker edges than the robert's operator.

## Sobel Operator
![[Pasted image 20230601040910.png]]
* Similar to the prewitt operator but the existence of the 2s creates a weighted average.

## Canny Edge Detector
* Actually detects edges instead of just detecting gradients. through a series of steps:
	1. Smooth the image with gaussian smoothing.
	2. Apply edge detection with any edge detection algorithm and calculate the gradient magnitude and direction for each pixel.
	3. Classify the edge normals into one of the following categories: 
		* Horizontal edge
		* Vertical edge
		* 45 degree edge
		* -45 degree edge
	4. Conduct non-maxima suppression by: 
		1. For each pixel, take its direction and the direction of its 8 neighbours.
		2. If 2 or more neighbouring pixels in the same direction have the same direction then set this edge normal's value to 0
	5. Classify the pixels as either a weak edge, strong edge or not an edge by choosing 2 arbitrary magnitudes $T_L$ and $T_H$ wherein: 
		* Magnitudes below $T_L$ are not edges.
		* Magnitudes in between $T_L$ and $T_H$ are weak edges.
		* Magnitudes above $T_H$ are strong edges.
	6. For every strong edge, set all the weak edges that neighbour it to strong pixels as well.
* In general, $T_H$ should be 3x higher than $T_L$.

