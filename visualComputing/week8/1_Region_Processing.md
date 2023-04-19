# Region Processing
* Is used to calculate the value of pixels using the values of adjacent pixels

## Edge Detection with Region Processing
* Vertical edge detection can be done with :
$$
I' = | I(x,y) - I(x+1, y) |
$$
* Eg the value of the pixel is the absolute value of the pixel minus the pixel to its right. 
* This however, creates a scenario wherein there is a line on the right edge of the image based on if the edges outside the image are given a value of 0.
* Another possible solution to the above problem is to chop off the rightmost pixels however this reduces the image size, making it a lossy process especially if multiple operations are done.
* To modify it for horizontal edge detection, the formula can be modified to compare the pixel with the one below it:
$$
I' = | I(x,y) - I(x, y+1) |
$$
* The edge problem now exists on the bottom edge.

## Combining Horizontal and Vertical Edge Detection
### Binary Images
* An `OR` operation can be done to combine the vertical and horizontal edge detections .
### Non Binary Images
* One of the following add operations can be used, followed by thresholding to remove noise.
* With city-block distance: 
$$
I' = | I(x,y) - I(x+1, y) | + | I(x,y) - I(x, y+1) |
$$
* With Euclidian distance: 
$$
I' =  \sqrt{(I(x,y) - I(x+1, y))^2 + (I(x,y) - I(x, y+1))^2)}
$$