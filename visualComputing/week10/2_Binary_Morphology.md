# Binary Morphology
* Used to solve the issue of if disjointed pixels are part of a blob but have been cut off due to thresholding.
* Can be either #dialation or #erosion 
* Uses `structuring elements` that are a set of pixels that can be in any shape.
* The structuring elements are then passed over an image one pixel at a time.
* Based on whether we are doing #erosion or #dialation, the action taken changes.

## Erosion
![[Pasted image 20230602023026.png]]
* If the centre of the structuring element is over an object pixel and any of the other elements of the structuring elements are over a background pixel, the centre also becomes background.
* The output for this process needs to be drawn into a new image. 
* This removes noise, removes bits that are sticking out and increases the size of holes within objects that are identified.
* Furthermore, it can also reduce the size of the objects.

## Dilation
![[Pasted image 20230602023208.png]]
* If the centre of the structuring element is background and any of the other elements are over an object, the centre pixel becomes part of the object.
* Removes holes within the image but also increases the size of the object.

## Preserving Object Sizes while Filling Holes
* Erosion makes holes larger while making objects smaller
* Dilation makes holes smaller while making objects larger.
* If we want the best of both worlds (small holes with the same size object) we can use either #opening or #closing That is the combination of both
	* Open(I) = dilate(erode(I))
	* Close(I) = erode(dilate(I))
* This also has tradeoffs as: 
	* opening will remove sticking out bits but also enlarge holes.
	* closing will fill in holes and fill out sticking out bits.