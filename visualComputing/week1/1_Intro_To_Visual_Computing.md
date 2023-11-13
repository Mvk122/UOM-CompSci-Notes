# Introduction to Visual Computing

## Raster Graphics
* All graphical representations are approximations.
* Some approximations, based on their techniques and resolutions are better than others in specific cases.

## OpenGL
* An open standard API specification designed to be `cross-architecture` for graphics programming.
* Separates the hardware layer from the software layer as it sits between the `application program` and the `display`/ `input devices`.
* Programming languages provide an API to the specific OpenGL version which talks to the hardware.
* Has support for rendering `lines`, `polygons` and `points`. 
* Has support for functionality like `shading`, `scaling`, `textures` etc.

## Graphics Pipelines
* Graphics pipelines are either `fixed-functionality` or `programmable`.

### Fixed Functionality
*  The algorithms of the pipeline cannot be changed, they can only be used by passing varied parameters to them.
* They're easy to use but are also older and deprecated.

### Programmable
* Some aspects of the pipeline can be modified by passing in code written in a `shading languge` eg (GLSL). This `shader` code is then run on the GPU as part of the pipeline.
* Is a newer method of doing graphics and is harder to use.

## GLUT
* Provides interaction with input devices and simple menu systems.

## GLU
* A `utility` library that sits between the `application program` and `OpenGL` to wrap up lower level OpenGL graphics.
* It also provides utility functions for `viewing`, `textures` and `tessellation`.
