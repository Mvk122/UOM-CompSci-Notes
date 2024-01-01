# Power Domains 
* Different parts of the chip may be powered from different voltages to allow for:
	* Slower regions to be run off reduced voltages. 
	* Depowering certain components when not in use.
* The interpretation of signals at power-domain boundaries becomes an issue when using multiple power domains but unlike clock-domains, this issue can be solved reliably.
	* The issue is caused with different interpretations of what is `high` in different power domains. I.e a high signal from a lower domain may be considered low in a higher domain.

## Level Shifter
![[Pasted image 20240102000249.png]]
* Used for shifting `high` signals between power domains.
* A low is always 0.0V so it does not need translation.

# Dynamic Voltage/ Frequency Scaling
* Power dissipation can be reduced by reducing the clock frequency due to less switching per unit time.
* The same amount of power is used per computation but there are fewer computations per unit time.