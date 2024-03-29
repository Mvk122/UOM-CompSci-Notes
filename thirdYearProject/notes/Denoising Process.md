## Steps Overview: 
1. Audio encoding to encode the audio into a format that can be used by the SNN
2. Denoising using the Spiking Neural Network 
3. Encoding the SNN output back into audio

# Definitions
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
* This generates a 2D vector, where we get a vector for the magnitude and phase shift (represented as a complex number) of each frequency bin for each frame of the audio.

## Hann Window and Spectral Leakage![[Pasted image 20240329172054.png]]
* Signals are rarely an integer number of periods hence the ends of the signal are discontinuous.
* This appears as high frequency components that aren't present in the original signal when a fourier transformation is applied.
* Hence this issue can be solved by applying a `hann window function` on the frame which eliminates the samples at the ends of the frame, leading to a periodic signal.
![[Pasted image 20240329172949.png]]
* However, due to the flat signal at the end of each frame, when we connect all the frames together, we have lost a lot of the signal.
![[Pasted image 20240329173034.png]]
* Hence when creating the frames, we overlap them slightly to their adjacent frames.
# 1: Encoding with Short Term Fourier Transformation
* Encoding via STFT is used to extract the magnitude and phase of each frequency bin over all `frames` from the audio. (2D Vector)
	* This is used instead of the raw audio as noise and signals often occupy different signal bands, hence transforming the audio to the frequency domain makes it easier to separate audio from noise and train a model on it.
* During the short term fourier transformation, we use the `hann window` function to prevent spectral leakage. 
	* `win_length` is set to `512` and `hop_length` is set to `128`, hence each frame is `512` samples wide and has `384` samples of overlap with its adjacent frames.
```python
# line 42 of src/preprocess.py
complex_stft = torch.stft(audio, n_fft, hop_length, win_length, return_complex=True, window=torch.hann_window(n_fft))
```
* The output of the short term fourier transform is a 2D vector of complex numbers, they are complex to represent the amplitude of the signals composing the wave as well as the phase shift of the sin waves.
* We don't care about the phase shifts, hence use `torch.abs` to get the absolute value, leaving only the `magnitude`.
* The `magnitude` is then normalised using `offline laplace norm`.
* The resulting normalised magnitudes of the STFT are passed to the neural network.

## References 
[Why does FFT give complex numbers](https://stackoverflow.com/questions/10304532/why-does-fft-produce-complex-numbers-instead-of-real-numbers)
[Short Term Fourier Transformation Explanation](https://www.youtube.com/watch?v=-Yxj3yfvY-4&t=1s)
[Extracting Features with STFT, Feature explanation, Hann Window](https://www.youtube.com/watch?v=8A-W1xk7qs8&list=PL-wATfeyAMNqIee7cH3q1bh4QJFAaeNv0&index=7)

# 2: Fullband Model
