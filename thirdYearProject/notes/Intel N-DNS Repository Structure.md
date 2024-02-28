# Terminology
* `Lava`: Software for developing neural networks in software https://github.com/lava-nc/lava
	* Pip needs to install `lava-nc` and `lava-dl`

# Lava_Inference.ipynb
* Jupyter notebook for encoding, denoising and decoding using the default neural network solution.
* Uses `../Trained/network.net` for the weights in the network.
# Microsoft-DNS
* Contains the audio samples for training, validation and test in `datasets_fullband`. Downloaded with `download-dns-challenge-4.sh`.

# DNSAudio (audio_dataloader.py)
* Loads the audio from the expected folder structure of the Microsoft DNS dataset.
* Uses sf.read to get:
	 1. **Audio Data**: This is a NumPy array where each element represents an audio sample. The shape of the array depends on the number of channels in the audio file. For a mono audio file, the array is 1-dimensional. For a stereo audio file, the array is 2-dimensional, where each row represents a sample and each column represents a channel.
	 2. **Sampling Frequency**: This is an integer that represents the number of samples per second in the audio file. This is often referred to as the sample rate and is typically 44100 Hz for CD-quality audio.
 * Has a `__getitem__` that gets the `nth` audio sample with padding such that it pads with 0s the sound files to ensure noisy_audio, noise and clean_audio are all of the same size.