# Illumination 

## Ambient Illumination 
![[Pasted image 20230529043600.png]]
* Creates an ambient lighting in the scene that is constant wherein the brightness of a surface is given by $I = I_a * k_a$ where $k_a$ is the reflectivity of the surface.
* This kind of illumination can make 3d objects look 2d as every surface is equally illuminated.

## Directional Lighting (Diffuse)
![[Pasted image 20230529044440.png]]
* Illumination from a point wherein both the angle of incidence and the distance from the light source change the level of illuminance of a surface.
* Thus the amount of diffuse reflected light will be:
$$
I_d = I_pK_dcos(x)
$$
* Where $Ip$ is the intensity of the incident light, $K_d$ is the diffuse reflectivity coefficient and $x$ is the angle of incidence.
* This can give the scene more of a 3d look than only ambient.

## Light Source Distance 
* The intensity from a light source scales with the inverse square of the distance in the equation: 
$$
I_e = \frac{I_p}{4πd^2}
$$
* It is physically correct but as the value of d gets smaller, the value of d^2 changes rapidly which is not good for approximation as there are a limited number of pixel intensities hence a different equation is used:
$$
I_e = \frac{I_p}{k_c + k_ld + k_qd^2}
$$
## Observed Specularity 
![[Pasted image 20230529045229.png]]
* Due to the fact that specular reflections have a range of reflections wherein the intensity of light reduces between the "optimal" reflected angle and the viewing angle, we can create an equation that captures this reduction in intensity with deviation from the angle of incidence.
$$
I_s = I_pcos^n(x)
$$
* Where $I_s$ is the amount of specular reflection, $I_p$ is the incident amount of light , x is the angle and $cos^n$ is arbitrarily chosen as a constant to choose how much the intensity should deviate.
![[Pasted image 20230529045553.png]]
* The values of n are generally between 1 and 200.