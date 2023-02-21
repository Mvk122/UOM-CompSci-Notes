* In computer graphics, there is no camera, it is simulated by transforming the model.
* The camera can be represented by 3 parameters:
	* `coordinate E`: The position of the camera.
	* `vector V`: The orientation of the camera, which is perpendicular to C.
	* `vector C`: The direction that the camera is pointing at.
* Let $T_c$  be the transformation that translates the camera from (0,0,0) looking down the Z axis to the above E, C, V.
* The inverse of $T_c$ can be applied to the models to give the illusion of the camera.

## Defining the Camera's Perspective
* The camera's perspective can be defined by 3 parameters analogous to the above:
	* `vector F_hat`: Pointing away from C, can be calculated with $normalise(E - C)$ 
	* `vector U_hat`: The normalised version of V
	* `vector S_hat`: Perpendicular to F_hat and V_hat.
* The user has to pass in V to calculate U but we cannot guarantee that it is perpendicular to F_hat which is required. Hence steps need to be taken to calculate a guaranteed orthographic U.
	* $\hat{S} = normalise(\hat{F} \times \hat{V})$
	* $\hat{U} = normalise(\hat{S} \times \hat{F})$

## Applying the Camera's Perspective
* With the vectors S, U and F, a transformation of the inverse of $T_c$ can be derived.
* First translate by $-E$
* Then rotate the camera axes to be coincident with the world axes with F aligned with $-Z$