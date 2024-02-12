> Relevant to [[3_Clocking]]
# Crossing from Slow to Fast Clock Domains
![[Pasted image 20240212161431.png]]
* Crossing clock domains from a slow to a fast clock can be done by passing the signal through a chained series of flip flops.
* There is always a risk of metastability, however it can be reduced by chaining more flip flops.

# Crossing from Fast to Slow Clock Domains
## Before
![[Pasted image 20240212162237.png]]
## After
![[Pasted image 20240212162256.png]]
* Crossing from a fast to a slow clock domain can lead to pulses being too fast for the slow clock to capture them.
* To prevent this, stretching can be used where the signal is stretched to ensure that the slow clock can capture it. 
* The minimum amount of clock cycles to stretch it to should be `2 * fast_clock/slow_clock`.

### Example Stretcher Verilog
```verilog
module stretcher(
    input wire fast_clock,
    input wire slow_clock,
    input wire signal_in,
    output reg signal_out,
    output reg enable // Can only stretch 1 signal at a time
);

    reg [7:0] signal_length = 0;
    reg [7:0] signal_output = 0;

    always @ (posedge fast_clock) begin
        if (signal_in) signal_length <= signal_length + 1;
        else if (signal_in == signal_out) signal_length <= 0;
    end

    always @ (posedge slow_clock) begin
        if (signal_length > 0 && signal_output != signal_length) begin
            signal_output <= signal_output + 1;
        end else if (signal_output == signal_length) begin
            signal_output <= 0;
        end else signal_output <= signal_output;
    end

    always @ (*) begin
        // works when signal in can only be 1
        // Will need to cache signal in and do a ternary otherwise
        signal_out = signal_output > 0; 
        enable = !signal_out;
    end

endmodule
```

# Streaming Data Between Clock Domains
* The above methods are useful for intermittent signals however when streaming data, a FIFO using block RAM should be used instead. 
* This is described in [[3_Clocking]]