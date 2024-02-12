> Relevant to [[3_Clocking]]
# Crossing from Slow to Fast Clock Domains
![[Pasted image 20240212161431.png]]
* Crossing clock domains from a slow to a fast clock can be done by passing the signal through a chained series of flip flops.
* There is always a risk of metastability, however it can be reduced by chaining more flip flops.

# Crossing from Fast to Slow Clock Domains
## Before
![[Pasted image 20240212162237.png]]
## After
![[Pasted image 20240212162256.png]]
* Crossing from a fast to a slow clock domain can lead to pulses being too fast for the slow clock to capture them.
* To prevent this, stretching can be used where the signal is stretched to ensure that the slow clock can capture it. 
* The minimum amount of clock cycles to stretch it to should be `fast_clock/`