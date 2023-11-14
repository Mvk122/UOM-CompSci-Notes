# Stylistic Pitfall 
```verilog
always @ (posedge clk)
	if (count < 9) count <= 1 + 1; else count <= 0;
```
* Due to the event driven architecture of verilog, non-blocking assignments occur after blocking assignments.
* Hence if the input, (count) is changed in a blocking assignment elsewhere in the code, that change will happen prior to this `if` statement even if it's condition is also `always @ (posedge clk)`.