# Time Stealing
![[time_stealing-removebg-preview.jpg]]
* In an unbalanced pipeline, some stages of the pipeline can take less time than others.
* In the above case, this leads to 200ps between the second stage of the pipeline completing and its output being sent to the register input.
* As a performance improvement we can do the following:
	* Increase the clock speed such that the clock period is actually 900ps.
	* Since 1000ps is still needed for the first stage, we can steal that time from the second stage in the form of a delay in the first stage's output register. This 900ps+100ps gives us the 1000ps we actually need.
	* Since the second stage only needed 800ps, we can afford the extra 100ps delay.
	* We now have a clock speed of 1.11GHz instead of 1 GHz.

## Challenges with Time Stealing 
* Standard design flows will not allow for this.
* There needs to be a well controlled delay in the clock distribution tree, in practice this is hard to achieve.
* There is a stricter hold-time bound on the first stage. It must be guaranteed that there is no scenario where it takes less than 100ps else it would be captured by the same clock signal that started it via the delay in the register.

## Time Borrowing
* Uses transparent latches which do not depend on the clock instead of edge triggered flip flops. 
* Hence the time saving can be automatic as complicated delay mechanics will not be required.