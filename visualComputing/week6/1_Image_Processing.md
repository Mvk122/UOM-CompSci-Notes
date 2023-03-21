# Image Processing
* A set of computational techniques for analysing, enhancing, compressing and reconstructing images.

## Image Representation
![[Pasted image 20230321073504.png]]
* Images are generally represented by a 2D grid of pixels in a matrix.
* The matrix starts at (0,0) in the top right.
* Pixels can have different definitions:
	* `color representation`: Each pixel contains 8 bits each for a value for red, green and blue.
	* `greyscale representation`: One byte per pixel stating the intensity of the pixel.

### Point Processing
![[Pasted image 20230321085831.png]]
![[Pasted image 20230321085844.png]]
* Point processing can be used for feature detection (finding objects relative to their background).
* For example, thresholding can be used on a certain channel (ie only the blue pixels) to state that pixels with a blue intensity above a certain amount are the object and are thus given the value of 255, and 0 otherwise.