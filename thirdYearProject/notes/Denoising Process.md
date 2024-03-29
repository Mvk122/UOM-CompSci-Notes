## Steps Overview: 
1. Audio encoding to encode the audio into a format that can be used by the SNN
2. Denoising using the Spiking Neural Network 
3. Encoding the SNN output back into audio

# Definitions
## Audio Features

## Sample
* A measurement of the amplitude of the audio signal at a specific point in time.
## Frame
- A `frame` is a perceivable audio chunk (10ms) in an audio file. A frame is needed as samples in audio i.e at 44.1KHz sample rate have a duration of only 0.0227ms. 
- Generally the amount of samples in a frame are a power of 2 as having a power of 2 samples makes the fast fourier transformation much faster

## Short Term Fourier Transform

![[Pasted image 20240328204431.png]]
* $d_f$ is the duration of the frame, $S_r$ is the sample rate and $K$ is the number of samples in a frame.
# 1: Encoding with Short Term Fourier Transformation
Encoding via STFT is used to extract `audio features` in the form of a ma `frames` from the audio.