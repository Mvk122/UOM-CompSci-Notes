## Scan Conversion
* The process of converting lines and polygons that have already been transformed into a 2D plane into approximate pixels on a screen.

### Scan Converting Lines (Bresenham's Algorithm)
* Start at 1 end of the line.
* Calculate based on the gradient, how much y must be increased based on an increase in x.
* So $y_{n+1} = y_n + m$, and $y_{n+1}$ is rounded to the nearest pixel.
* x and y will need to be swapped based on the gradient of the line.

### Scan Converting Polygons
* The $(x,y)$ coordinates of the polygon's vertices correspond to pixel positions on the screen.

#### Scan Converting Naively
* Process each row of pixels, if it is an interior pixel then fill it in.

#### Scan Converting (Sweep Line)
* Calculate the gradients of the lines making up the polygon.
* Get the start and end points by iterating from the bottom of the polygon up, using the gradients to adjust the start and end point at each iteration.
* Iterate between the start and end points, filling in the pixels.

## 