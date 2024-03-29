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
![[Pasted image 20240328204431.png]]
* $d_f$ is the duration of the frame, $S_r$ is the sample rate and $K$ is the number of samples in a frame.

## Short Term Fourier Transform
![[Pasted image 20240329170953.png]]
* A fourier transform transforms a time/amplitude domain to a frequency/amount domain, which shows the number of signals at each frequency-range.
* The problem with the discrete fourier transformation is that we lose all of the time information which is important when analysing the changes in frequencies over time.
* A short term fourier transformation applies a fourier transformation over each `frame` of the audio.
* This generates a 2D vector, where we get a vector for the amount of signals in each frequency bin for each frame of the audio.
# 1: Encoding with Short Term Fourier Transformation
* Encoding via STFT is used to extract `audio features` in`frames` from the audio.
	* Essentially creates a 2D image which is easier to 
* The output used is the magnitude of the short term fourier transformation.
* During the short term fourier transformation, we use the `hann window` function to prevent spectral leakage. 
```python
# line 42 of src/preprocess.py
complex_stft = torch.stft(audio, n_fft, hop_length, win_length, return_complex=True, window=torch.hann_window(n_fft))
```