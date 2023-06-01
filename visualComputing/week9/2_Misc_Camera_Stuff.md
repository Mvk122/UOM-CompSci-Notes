# File Formats
* Different file formats are used to store different types of image data.
* Eg a `portable bitmap` only stores pixel values of 1 and 0 hence 8 pixels can be stored in 1 byte, allowing for 8x greater compression.

## Exposure
* Cameras are able to vary the lighting conditions that they can capture images from by changing either:
	* `Aperture`: Covers the lens partially to vary the amount of light allowed into the lens. A large aperture can reduce the depth of field (bokeh effect).
	* `Camera Shutter`: Changing the amount of time that the camera shutter is open, altering the amount of light arriving on the lens. However, a low shutter speed can cause motion blurring.
* `High Dynamic Range` can show a larger range of brightness in an image by taking many photos at different exposures in sequence and combining them.

## Colour Palette
* There are many ways for colours to be represented and there is a choice to be made in the trade off between storage requirements and fidelity.
### GIFs
* Only 8 bits per pixel but can contain any colour from the 24 bit colour space. Though due to the 8 bits per pixel limitation, only 256 colours from the 24 bit colour space can be used in any given image.
* Hence when storing GIFs, the image data needs to be stored as well as the palette which represents what colour each unique byte in the image represents.
### Transparency
* Formats like PNG have additional bits for their `alpha` channel which represents the transparency.