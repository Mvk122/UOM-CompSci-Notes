![[Pasted image 20230419150429.png]]
* A convolution is an operation wherein the pixels surrounding the target pixel are multiplied by their corresponding pixel on the `kernel`. The values are added up and the value of the centre pixel is given the value of this summation.
* For pixels where the kernel gets cut off (at the edges), we can either:
	* Only calculate for pixels not at the edge/corners, effectively shrinking the image by 2 pixels horizontally and diagonally.
	* Assume values outside the image are 0.
* This cannot be done in place because a pixel to the right of a pixel that was just convoluted would be taking the value of the computed convolution for the first pixel.
* The technical definition of a convolution is when the top left of the kernel multiplies with the bottom right of the pixels and so on (flipped diagonally), the non-flipped definition is a correlation however most software uses the correlation definition for convolutions.

## Convolution Optimisation
![[Pasted image 20230419150920.png]]
* Convolutions are associative, this can be used to reduce the amount of computation needed for a convolution.
* Thus a 3x3 convolution that can be done with 9MN computations can be replaced with 2 convolutions, of size 1x3 and 3x1 for only 6MN computations.
* The efficiency gain with this technique is much larger for larger convolution kernels.

## Uses of Convolutions
* Convolutions can be used for:
	* Image Sharpening
	* Image Smoothing
	* Laplacian edge detection