## Decade Counter Example 
![[count_10_a 1.png]]
* The aim: To have a counter that counts from 0 to 9 and then straight back to 0, with a signal called `rc` that has a `negedge` every 10 counts.

## Assigning RC using Combinatorial Logic
![[count_10_b.png]]
```verilog
always @ (posedge clk)
	if (count < 9) count <= count + 1;
	else count <= 0;
	assign rc = (count == 9);
```
* Using combinatorial logic can cause glitches as they are `level sensitive` as opposed to `edge sensitive`. 
	* They are more sensitive as they are sensitive to the level of the clock signal which can change at any time as opposed to `edge sensitive` circuits which are only sensitive to rising or falling of the edges of inputs.
* Since the `rc` is assigned at the same time as count is assigned to 9, there is a delay in assigning and un-assigning it, making it not in sync with the clock.

## Assigning RC using Sequential Logic
![[count_10_c.png]]
```verilog
always @ (posedge clk)  
if (count < 9) count <= count + 1;  
else           count <= 0;  
   
always @ (posedge clk) rc <= (count == 8);
```
* Does not have glitching and occurs on the clock edge as the inputs for the computation are set before the clock edge.