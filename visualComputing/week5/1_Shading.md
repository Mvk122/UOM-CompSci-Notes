# Shading

## Flat Shading
![[Pasted image 20230529052200.png]]
* Works out a shade for each triangle/surface on a mesh and applies the same shade for the entire triangle.
* Is very bad as due to the `Mach Band` effect, humans can clearly see the mesh due to the human vision system being very good at spotting edges.

## Gouraud Shading
![[Pasted image 20230529060127.png]]
* Uses interpolation to smooth out the discontinuities between polygons.
* Gets the average surface normal for a vertex by taking the average of the surface normals for the surfaces around the vertex.
* It then interpolates the values of the pixel colours over the surfaces between the vertexes.
* This makes curved surfaces look more curved.
![[Pasted image 20230529060329.png]]
* There are problems with gouraud shading however: 
	* It flattens out highlights.
	* The mesh is still visible on surfaces on the edges of a model that are not connected in all sides to other surfaces.

## Phong Shading (Normal Vector Interpolation)
![[Pasted image 20230529061334.png]]
* Instead of interpolating colours over the surface, we interpolate normals (calculating a new normal for each pixel) and then apply the local illumination model to each of the pixels.