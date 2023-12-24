## Blocking VS Non-Blocking
```verilog
// Use non-blocking on clock signals
always @ (posedge clk) begin
	a <= c + 5;
	b <= a + 2;
end

// Use blocking for always @ *
always @ (*) begin
	a = c + 5
	b = c + 5 + 2;
end
```