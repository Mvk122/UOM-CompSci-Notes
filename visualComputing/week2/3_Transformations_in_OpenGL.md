# Transformations in OpenGL

* OpenGL maintains 2 transformation matrices internally.
* The final image, `P drawn` = `ProjectionMatrix` * `ModelViewMatrix` * `P specified`

## ModelView Matrix
* Used for transforming the geometry and specifying the camera.

## Projection Matrix
* Controls the way the camera image is projected onto the screen.