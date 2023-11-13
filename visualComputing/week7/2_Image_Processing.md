# Image Processing

## Image Histograms
* Image histograms can be created by plotting a discrete variable against the frequency of each.
* Eg the frequency of each grayscale value for a grayscale image.
### Brightening Images
* When images are `brightened` by a constant, the image histogram moves to the right by the constant amount. This leads to a loss in data as points reach the max brightness value and are clipped.
### Increasing Image Contrast
* The contrast of an image can be increased by multiplying each pixel's brightness by a constant.
* This can leave gaps in the histogram due to rounding and levels being skipped eg when multiplying by 2, there will be no pixels with an odd brightness.

## Input Output Mapping
* A lookup table can be used to create an input output mapping for a custom brightness/contrast adjusting algorithm.
* Furthermore, piecewise functions can be used instead of a lookup table.

### Min-Max Linear Stretch
![[Pasted image 20230321125456.png]]
* Anything below the minimum is set to 0
* Anything above the maximum is set to the highest value.
* Anything in between has its contrast increased as the line has a gradient above 1.
### Thresholding
![[Pasted image 20230321125611.png]]
* Anything below the threshold `T` is set to 0
* Anything above is set to the max value.

## Thresholding Algorithms
* Thresholding algorithms are used to determine the right value for the threshold `T`. There are many algorithms for this.
* However, there is often an overlap between what can be considered background and objects. Hence there will always be false positives of the background and false negatives of objects.
### Percentile threshold
* If it is known that the desired object takes up a certain proportion of the image, the threshold can be set on the image histogram where there are $proportion \times totalPixelsInImage$ pixels before the threshold on the histogram.
### Average threshold
* Where the average intensity below the threshold is the same as the average intensity above the threshold.

## Interpolation
* Interpolation is needed in scaling to fill in pixels that have no values when an image has been scaled or rotated.
* There are many ways to do interpolation for scaling:
	* `Nearest Neighbour`: The blank pixels take the value of their nearest neighbour eg when scaling by 2, the 3 pixels created take the value of the 1 pixel in the top left. This creates blocky artefacts.
	* `Linear`: Choosing a colour linearly between its neighbours.
	* `Cubic`: Same as linear except using a cubic function.
* For `rotation`, not all pixels in the source have a location in the destination due to non-integer rotations. Thus instead of  cycling through source pixels, cycle through destination pixels to get their corresponding source pixel.