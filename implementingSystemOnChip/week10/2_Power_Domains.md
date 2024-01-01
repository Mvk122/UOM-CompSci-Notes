# Power Domains 
* Different parts of the chip may be powered from different voltages to allow for:
	* Slower regions to be run off reduced voltages. 
	* Depowering certain components when not in use.
* The interpretation of signals at power-domain boundaries becomes an issue when using multiple power domains but unlike clock-domains, this issue can be solved reliably.