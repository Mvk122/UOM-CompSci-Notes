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
* A H-Tree is used to distribute the clock signal, ensuring that each component in the chip is connected at the same "level" of the tree to minimise clock skew.
	* `Clock skew`: The difference in arrival time of the clock signal from one part of the processor to another.
* Generally the high fan-out requires amplification/ buffering as:
	* Clock edges should be fast to decrease the uncertainty in when the transition occurs.
* The amplification/ buffering strategy works as:
	* Clock signals are repetitive so the latency doesn't matter. 
	* They always arrive at regular intervals.

## Timing Closure
![[Pasted image 20231227174131.png]]
* Fitting all the logic into the desired clock period.
* Can be assisted by `static timing analysis` tools which deduce the logic paths by finding the registers and estimating the signal delays through all paths.
* The output is the slowest path which is the limiting factor in the circuit. Finding this critical path can be hard to achieve through simulation, however as it is not guaranteed that the critical path is simulate.

