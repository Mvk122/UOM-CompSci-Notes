# Timing 

## The Clock Model
* Using a clock to synchronise all operations in a chip.
### Advantages
* Leads to a significant simplification of the design in a functional block.
* Allows for FSMs where a snapshot of the current state and inputs can be used to derive the next state.
### Disadvantages
* Keeping everything synchronous can be challenging.
* Keeping within the clock period is an additional constraint.
* Crossing clock domains needs to be accounted for.

## D Type Flip Flop 
```verilog
module d_flip_flop (
    input wire d,
    input wire clk,
    input wire read_enable,
    output reg q
);
    always @(posedge clk) begin
        if (read_enable) begin
            q <= d;
        end
    end
endmodule
```
* In theory the transfer between D and Q should be instantaneous on a clock edge however in the real world the following need to be accounted for:
	* `Data set up time`: Data stability before the clock.
		* This can be easily accounted for as it depends on the intervening logic from one clock edge to the next being sufficiently slow, hence violations can be solved by clocking the processor down.
	* `Data hold time`: Data stability after the clock.
		* This is hard to account for as it depends on not passing through any intervening logic too quickly after a clock edge such that it affects subsequent flip-flops at the **same** active clock edge hence it cannot be accounted for externally.
	* `Propogration Delay`: Output lag after the clock.

## Clock Distribution
![[Pasted image 20231227165833.png]]
