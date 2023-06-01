* Blobs are a set of pixels that share some property and are connected.
* In more formal terms, adjacent pixels need to have similarity to be considered as part of the same blob.

## Blob Detection
![[Pasted image 20230601071729.png]]
* There can be many distinct features in an image, blob detection is used to separate each feature out individually.
* It is done in 2 passes:
	1. For each pixel that is identified as part of a feature label it as such:
		* If 0 of its neighbours have a label, give it the next free label.
		* If 1 or more neighbours have the same label, give it the same label.
		* If 2 or more neighbours, give it any one of the labels but mark down this equivalence.
	2. Relabel all equivalent labels eg if there is a 3 next to a bunch of 1s, relabel it as 1.
* Thresholding is used to get the features in the first place, this can however lead to parts of the features being cut out, thus creating additional blobs from disconnected parts of the image. 
* This can be resolved by using either `dialation` or `erosion` (opening or closing).

## Blob Boundary Detection
* Once blobs have been marked, their boundaries can be formed via the following steps:
1. Scan the image from left to right and top to bottom.
2. On reaching the first object pixel, save its location as $O_0$. The pixel to its left becomes $B_0$.
3. Search clockwise for other objects, on finding one label it $O_1$ , jump to it and look clockwise for other object pixels.
4. Continue this process until reaching $O_0$ again and the next pixel is $O_1$. When that happens, a loop has occurred and the boundary has been formed.
	* The condition of $O_1$ being the next pixel is required to ensure that $O_0$ was not found again as part of a sub-loop.

## Moment of Area
![[Pasted image 20230601155749.png]]
* We can calculate the "centre of gravity" of a blob by averaging the x and y positions of all the pixels in the blob.
* In the formal definition, we can substitute alpha and beta with values to extract different uses from the blob such as:
	* Letting both equal 0 gives the sum of pixels.
	* Letting (a, B) = (1,0) gives the sum of x values for the region's pixels.
* We can use this metric to get the orientation of the region with:
$$
\frac{1}{2}tan^{-1}(\frac{2M_{11}}{M_{20} - M_{02}})
$$

## Chain Codes
![[Pasted image 20230601160625.png]]
* Chain codes are codes that place directions (they have to be in the 4 cardinal directions and the diagonals)  onto pixels to encode the boundary of a blob.
* They are used as they are a much more compact representation of blobs as they use much fewer bits for any given blob.
* Since chain codes would be unique if the blob is rotated, we can use `differential chain codes` to get the same code for a given blob in any of its rotations.
* This is done by starting at the same pixel and just encoding the difference in the direction of the current pixel from the previous pixel (eg in the current diagram, the first one will be 2 and the second will be 0).
* An alternative to calculate the `differential chain code` is by iterating through the chain code wherein $C_{n} = C_{n-1} (mod (8))$
* The `Permieter` of the chain code can be done by summing the values of each number in the chain wherein:
	* Even numbers have a value of 1
	* Odd numbers have a value of $\sqrt{2}$

## Area of a blob
* Both of these methods calculate the values of a polygon that would be made by the outline of the blob. Thus they will underestimate the size of the blob.
* The effect of the discrepancy will be reduced as the size of the blob gets larger.
### Area from Pixel Values
* The `Area` of the blob from the pixel values can be calculated using the `shoelace algorithm`.
![[Pasted image 20230601161825.png]]
 * The total area is $\frac{sum}{2}$

### Area from Chain Codes
![[Pasted image 20230601162055.png]]
* Using the shoelace algorithm except that the values for x and y refer to the increment and decrement of the pixel value from each element in the chain code based on the direction of the chain code (eg bottom left is -1 for x and -1 for y)

## Blob Matching
* Blob matching can be cone by taking account the position and velocity of a blob compared to itself in previous frames.
* Then by taking an invariant of the blob (something that doesn't change), try to find a blob near the predicted location with the same invariant.
* This can be challenging due to: 
	* Changing velocity (wrong velocity estimate)
	* Invariants changing due to changes in lighting/orientation
	* Multiple blobs at the predicted location.
	* No blob at the predicted location
	* Blobs appearing where there was no prediction. 