```verilog
module mux4to1(input wire signals[3:0],
			   input wire sel[1:0],
			   output reg out);

always @ (*) begin
	out = signals[sel];
end
endmodule
```
* When implementing a 4-to-1 multiplexer using LUTs, we need a LUT or combination of LUTs that takes in 6 inputs (4 for the mux input signals and 2 for the select signals).
* This requires a mask of $2^6$ bits and the output assignment would be:
```verilog
always @ (*) begin
	y = lut_mask[{sel, signals}];
end
```
