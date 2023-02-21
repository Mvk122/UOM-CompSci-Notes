* `hidden surface removal` is used to only calculate polygons that are not blocked by polygons ahead of them.

## Hidden Surface Removal with Z-Buffer
* For each pixel in the display memory, there is a corresponding entry in the Z-buffer.
* For each pixel generated during scan-conversion, if the pixel's Z coordinate is lower than the current Z-buffer, render it and set the Z buffer at the pixel's location to the pixel's Z coordinate.
* A lower Z-coordinate means the pixel is closer to the camera.

## Problems with Z-Buffer
* Lack of precision in the Z-buffer leads to incorrect rendering of pixels with similar z-values.
* This can lead to Z fighting where the pixels are calculated to be the closest interchangeably between frames.