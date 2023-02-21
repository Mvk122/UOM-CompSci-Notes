* Are an ordered set of vertices that create a shape that is bounded by the vertices.
* In OpenGL, polygons need to be convex hence all interior angles sum to less than 180 degrees.
* In general when representing 3D models, they are usually triangles.

## Representing Scenes with Polygons

### Polygon Soup (Bad)
* Having a list of individual polygons that are coloured individually and drawn in order.
* They are a waste of space as vertices are duplicated as most models are made of surfaces of connected polygons.
* Without a hierarchy, semantic information about which object a polygon belongs to is lost.
* It makes interaction with the model difficult due to this unclear surface information.

### Polygon Meshes
* Uses linked groups of polygons or `meshes` to represent surfaces.
* It retains semantics of surfaces and reduces storage by sharing vertices and edges.
* Has many implementations:
#### Triangle Strips
![[Pasted image 20230221141947.png]]
* Create 2 initial vertices.
* Every time a new vertex is added, a new triangle is created with the vertex and the edge of the previous triangle. 
* N triangles can be represented with N+2 vertices.

#### Triangle Fan
![[Pasted image 20230221142302.png]]
* Create an origin vertex.
* Create 2 vertices for the first triangle.
* Each time a new vertex is added, use the edge of the previous triangle to the origin and the new vertex to create a new triangle.
* N triangles can be represented with N+2 vertices.

#### Quadrilateral Strips
![[Pasted image 20230221142521.png]]
* Are tessellated into triangles during rendering.
* $N \times M$ quads can be defined using $N+1 * (M+1)$ vertices.