# Time Stealing
![[time_stealing-removebg-preview.jpg]]
* In an unbalanced pipeline, some stages of the pipeline can take less time than others.
* In the above case, this leads to 200ps between the second stage of the pipeline completing and its output being sent to the register input.
* As a performance improvement we can do the following:
	* Increase the clock speed such that the clock period is actually 900ps.
	* Since 1000ps is still needed for the first stage, we can steal that time from the second stage in the form of a delay in the first stage's output register. This 900ps+100ps gives us the 1000ps we actually ne
	* 