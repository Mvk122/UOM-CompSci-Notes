# Noise
* There are 2 definitions: 
	* Anything within the imaging system that causes a change eg electrical interference (preferred definition).
	* Anything that causes a change eg atmospheric disturbance.

## Noise Reduction Techniques
### Smoothing
![[Pasted image 20230419151933.png]]
* Since noise is random with a zero mean, smoothing will be able to reduce noise.
### Local Smoothing
![[Pasted image 20230419152111.png]]
* By using a convolution to do smoothing.
* This technique removes detail and introduces ringing (artefacts on the edges of sharp transitions)
### Smoothing Temporally (over time)
* Taking an average of many images.
### Adaptive Smoothing
* For each pixel, compute the smoothed value but take it only if it is not too different from the original value.
## Rank Filter (Median Filter)
* Similar to a convolution, however the centre pixel is given the median of the values of itself and the surrounding pixels.