# 2016 Example Paper

1. c 
2. a
3. d
4. b
5. a
6. d

## Short Answers
1. Modelling refers to constructing a digital representation of an object, rendering refers to displaying the model visually
2. It will not be trivially possible to do displacement with only a simple multiplication, thus making displacement transformations much harder.
3. The camera sets the viewpoint as well as parameters like near field, far field, FOV etc to render the 3d model into a 2d image/ video to be rendered.
4. The following steps can be done:
	1. Finding a matrix for the following transformations:
		1. displacing b so that it starts at the origin 
		2. Rotating B so it is coincident 3with the XY plane
		3. Rotating B so that it lies on the X axis.
		4. A scaling matrix for the s t u scaling.
		5. The inverse of (1* 2 * 3 )
	2. Multiply the 5 matrices above.
	3. This new matrix can be applied to any object now.
5. The near plane is a boundary where any objects nearer to the camera than the near plane will not be rendered. The far plane is a boundary where any objects further than it from the camera will not be rendered.
6. idk
7. A vector with a magnitude of 1. It can be used as a surface normal for a polygon to get the direction that it is facing.
8. They are used to concatenate matrices. This is useful for when there is a transformation that needs to occur many times on an object with respect to another object (eg the wheels need to move in tandem with the car)
9. Scaling by (0, b, c) and displacing by (p, q, r)
10. This is used when the pixels are smaller than texels during rendering of textures and is used to prevent the image from looking blocky. Interpolation is done by giving the pixel the average value of the texels around it.
11. It stores the counts of the various intensities that pixels can have in an image.
12. This could lead to brighter parts of the image falsely getting recorded as part of the object. To prevent this, we can change the threshold value throughout the image.
13. A convolution uses a kernel of NxN wherein the kernel is placed on each pixel of the image to create a corresponding output value for each pixel wherein the value of the pixel when it is at the centre of the kernel is the summed up value of each of the kernel's values multiplied with the value of the surrounding pixels. (This is the traditionally used meaning of convolution, the proper definition is when the top left of the kernel refers to the bottom right pixel and so on.). Special consideration needs to occur at the boundaries of the image as they will not have neighbours on 1 or more sides hence a decision needs to be made whether to chop them off or assume values around the image are 0. The resulting image is one that highlights similarities between the kernel and the image.
15. Thresholding can be used to separate the flooded areas from the non-flooded areas. To prevent noise, smoothing can be used beforehand using a rank filter and smoothing. Furthermore, the right thresholding value is needed and this can be found by comparing different threshold values on already labelled images. Validation can also be done by comparing to manually labelled images.
16. The primitives are red, green and blue and they have been chosen as they represent the 3 bands of lights that human eyes are most sensitive to.
17. ildk