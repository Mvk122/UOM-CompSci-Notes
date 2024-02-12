* an FPGA is comprised of `Configurable Logic Blocks (CLBs)` 
* The `CLBs`  are connected to each other through the `Switch Matrix` which also connects them to the I/O and the clock.
* `CLBs` are comprised of `Slices`.
* `Slices` are then comprised of `Look Up Tables (LUTs)`, `Flip Flops` and `Multiplexers`.

## What are Lookup Tables?
![[Figure2_LUT.webp]]
* Lookup tables are hardware which encode a truth table, wherein `n` inputs map to `m` outputs. 
	* In general, FPGAs nowadays use 6 inputs to 1 output LUTs.
* During initialization, the `LUT Mask`, which maps the inputs to the outputs is set on the SRAM bits of the LUT. 
* The actual inputs to the LUT are the select signal for the mux.
* For `n` inputs, a $2^n