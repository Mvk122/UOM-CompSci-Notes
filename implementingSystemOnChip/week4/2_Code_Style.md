## Decade Counter Example 
![[count_10_a 1.png]]
* The aim: To have a counter that counts from 0 to 9 and then straight back to 0, with a signal called `rc` that has a `negedge` when the counter is 9.

## Assigning RC using Combinatorial Logic
```verilog
always @ (posedge clk)
	if (count < 9)
```