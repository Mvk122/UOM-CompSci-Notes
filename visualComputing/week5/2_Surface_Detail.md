# Surface Detail

## Texture Mapping 
* Mapping either a pre-made image or a generating an image (procedural) to wrap around a mesh.
* When using an image as a texture, we refer to its pixels as texels.

## Performing Texture Mapping 
1. Start by associating each texture coordinate with each vertex of a polygon.
2. Interpolate the texture coordinates during scan conversion
3. Blend the pixel colour with the texture colour.

## Resolution Mismatches
* When the resolution of the pixels and the texels are different, sampling is required.
### Pixel Resolution > Texel Resolution
* When the pixels are smaller than the texels, we can simply select the texel to which the pixel matches.
* This is not ideal however as the resulting rendering looks blocky.
* Alternatively, `bilinear interpolation filtering` can be used wherein we compute a texel color from adjacent texels, averaging horizontally and vertically. This makes the image look smoother.
### Pixel Resolution < Texel Resolution
* In this case, adjacent pixels may map to texels far apart, leading to missing detail.
* This can be solved by using `mipmap` filtering wherein a set of textures are used wherein there is an original texture and a series of smaller images of the same texture generated by down sampling.
* The right texture is then used based on the size of the mesh on the screen.
* Another method is to choose the 2 closest textures and do binary interpolation.