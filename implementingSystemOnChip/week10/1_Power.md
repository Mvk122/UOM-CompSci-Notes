# Power
* Power is a concern due to:
	* Cooling concerns.
	* Energy demands on batteries for mobile equipment.

# Types of Power Dissipation
![[Pasted image 20240101235106.png]]
## Active (Dynamic)
* Done when switching due to charging/discharging load capacitance. 
* Depends on: 
	* the network load
	* the square of the supply voltage
	* The amount of activity
## Short Circuit (Dynamic)
* Done when both the `pMOS` and `nMOS` are active at the same time during switching as while one turns on, the other turns off.
* Depends on: 
	* The transistor threshold voltage (depending on the doping material). Higher means less power usage. 
	* The input voltage. 
	* The switching speed.
## Leakage Current (Static)
* Leakage of charge from the gates to the substrate. 
* Depends on:
	* The input voltage. 
	* The transistor threshold voltage.

# Transistor Thresholds
![[Pasted image 20240101235131.png]]
* The gate voltage in which a transistor switches from off to on.
* Measured from gate to channel (source or drain).
* Depends on the dopant concentrations.
* With lower thresholds:
	* The `nMOS` pull down switches earlier. (Turning on earlier). 
	* The `pMOS` switches off later.
* This leads to a longer duration for the short circuit, thus having a faster system but more power hungry.

# Power Gating
![[Pasted image 20240101235143.png]]
* Low leakage devices can be used to `power-gate` high speed logic wherein a special local supply current is passed to the `gated` circuit through the low leakage device.
* This ensures that power is only sent to the gated circuit when needed and it is powered off when not needed.
* The switching time is necessarily slow to allow for time to repower the gated supply.