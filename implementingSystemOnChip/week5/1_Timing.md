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
