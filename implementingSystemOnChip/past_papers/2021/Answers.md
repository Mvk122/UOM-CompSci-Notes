# 1a
* x: Either unknown or don't care, means that the value was not set. 
* z: high impedance, a wire is not being driven by any circuits.

# 1b
* They are not handled, delays are not synthesizeable. 
* Can be used to:
	* Model real components that have delays.
	* To make waveforms easier to read (aesthetic)
	* To sequence I/O in a test run.

# 1c
XX = 12
YY = 12
WW = 12

# 1d
x = 9
y = 10

# 2a
* For pMOS and nMOS it is the voltage at which they start conducting voltage through them. 
* The voltage at which above it is considered a 1 and below is considered a 0.

# 2b
* Transistors with a high threshold will be used as there will be less time at which the pMOS and nMOS are both conducting, hence less current lost due to short circuit.

# 2c
TODO

# 3a
* To reduce the probability that data is read from the latch while the latch is being written to, thus causing an error due to metastability. This is known as syncing the data.
* Furthermore, if block 2 is sampled at a higher frequency than block 1 is giving valid data, block 2 will be sampling incorrect data values.

# 3b
* Using a series of flip flops in series to latch valid values.
* If there is a harmonic relationship between the clocks, we can use 