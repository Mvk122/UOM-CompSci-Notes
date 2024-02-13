[[2_D_Type_Flip_Flops]]
* A latch is a level sensitive design wherein when the enable is active, the output continually matches its state to the input
```verilog
module latch(wire enable, wire [31:0] in, reg [31:0] out);

always @ (*) begin
	if (enable) out = in;
end

endmodule
```
* A flip flop is an edge sensitive design which only updates its state at the rising or falling edge of a clock signal. 