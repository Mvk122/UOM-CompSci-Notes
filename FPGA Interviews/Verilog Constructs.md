## Blocking VS Non-Blocking
```verilog
// Use blocking on clock signals
always @ (posedge clk) begin
	a = c + 5;
	b = a + 2;
end

// Use non blocking for always @ * (combinatorial)
always @ (*) begin
	a <= c + 5
	b <= c + 5 + 2;
end
```