* an FPGA is comprised of `Configurable Logic Blocks (CLBs)` 
* The `CLBs`  are connected to each other through the `Switch Matrix` which also connects them to the I/O and the clock.
* `CLBs` are comprised of `Slices`.
* `Slices` are then comprised of `Look Up Tables (LUTs)`, `Flip Flops` and `Multiplexers`.

# What are Lookup Tables?
![[Figure2_LUT.webp]]
* Lookup tables are hardware which encode a truth table, wherein `n` inputs map to `m` outputs. 
	* In general, FPGAs nowadays use 6 inputs to 1 output LUTs.
* During initialization, the `LUT Mask`, which maps the inputs to the outputs is set on the SRAM bits of the LUT. 
* The actual inputs to the LUT are the select signal for the mux.
* For `n` inputs, $2^n$ bits are required for the `LUT Mask`.

# Lookup Table Implementation in Verilog
```verilog
module lut2(input a[1:0], output reg y) 

reg [3:0] lut_mask;

initial begin
	lut_mask = 4'b0001; // LUT for an AND gate
end

always @ (*) begin
	y = lut_mask[a];
end
endmodule
```
* The LUT mask for an AND gate is 0001 as that would be when a is 11 in binary, thus takes the value of the 3rd bit of the mask which is 1.