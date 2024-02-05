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

## Why use Blocking vs Non-Blocking
* Non-blocking should be used on `always @ (posedge clk)` such that we can always determine the state after the clock edge as a function of the state before the clock edge. Blocking statements will take to resolve and can lead to glitches.