# Template Matching
* Used to find the location of a sub-part of an image within the larger image.
* This can be done by:
1. Using the template image as a convolution (the opposite meaning eg top left to top left).
2. Since the template is multiplied by the pixel values of the image, bright parts of the image could result in false positives as large numbers get multiplied, thus the final value should be normalised with the sum of the weights of the area the template is convolving with.
![[Pasted image 20230601051531.png]]
3. After thresholding the image, potential locations matching the template should appear.
* This is not very good at matching objects however as it wouldn't work if:
	* The template was modified in any way eg rotated, resized.
	* If we were using the template matching to find an object and not a pixel perfect replica of an object eg detecting the presence of a certain person's face, given another photo of them.