# Chip Packaging

## Pad Rings
![[Pasted image 20240108121117.png]]
* Are a form of external contacts that are placed on the periphery of the device.
* Are necessarily large as: 
	* They need to be large enough for a bonding machine to attach a wire.
	* They need to have amplification circuitry to drive off-chip signals.
	* They need to have circuitry for electrical protection
### Advantages
* Are simpler to manufacture as compared to flip chips.
### Disadvantages
* A logically simpler chip might be "pad limited" as in when the pads are placed and spaced, the central core area is not filled.
	* This wasted silicon costs a lot of money.
### Complications
* Since many boards may have numerous peripheral devices on board, not all of which are used concurrently, to save on pad size, these functions can be multiplexed onto the same pads, reducing the pad count.
	* This also allows for the chip to be less specific to certain functions, so fewer devices have to be built and tested.
## Flip Chips
* An alternative to pad rings wherein the pads are `micro-bumps` on the top of the passivation of the circuit and the chip is mounted upside-down in the package.
### Advantages
* Less wiring distance is needed from the chip to the bumps as opposed to wiring to the pad ring.
* More contacts can be made than just around the edge.
* Less noise as the wires are shorter. This is most important in long thin wires.
## Mixed Simulations
![[Pasted image 20240107190609.png]]
* It is infeasible to simulate a whole SoC in one run, hence different levels of simulation are done for different blocks.
## SPICE
* A circuit activity simulator that solves differential equations to give an accurate model on the behaviour of a circuit when it is fabricated.
* It takes in:
	* The netlist.
	* An input stimulus file.
	* Detailed models of the component's characteristics.
* SPICE simulations take a lot of time hence they are generally used on smaller circuits/ smaller portions of circuits to `characterise` and produce simplified standard cells, specifying:
	* Propagation delays.
	* Output edge speeds. 
* The standard cells are then used in larger analogue simulations.

## Place And Route
* Placement is the act of mapping cells onto the surface of the silicon so they are as close as possible but not overlapping. 
* There are constraints on the placement of cells:
	* Cells that are connected together should be placed adjacently.
	* They cannot be too close and have 100% utilisation as:
		* Space needs to be kept for routeing.
		* Space must be kept for later modifications such as buffer insertion.
* Wires from routeing have the following properties:
	* They cannot overlap. (They need to use multiple layers)
	* The preference is to use lower layers only to minimise parasitic load capacitance.

## Buffer Insertion 
* When a network is routed, it may be discovered to have excessive capacitance, resulting in slower edges. This is especially common on long data busses. 
* Hence electrical amplifiers have to be placed at certain intervals. This requires space close to the wiring and is why P&R cannot have 100% utilisation.
* Pros of buffer insertion:
	* They save time by speeding up edges.
	* They improve electrical integrity by making the circuit less susceptible to noise.