```verilog
module test (
    input int A, B, C,
    input logic X, clk,
    output int S);

always @ (posedge clk) begin
    if (X==1) begin
        S <= A;
    end else begin
        S <= B + C;
    end
end
endmodule
```

## Explain which signal path mainly limits the max clock frequency.
* The path where X != 1 as an additional add needs to be done before setting S, hence an additional adder is needed which is not present in the other paths

## Rewrite the code such that the max clock frequency can be increased.
```verilog
module test (
    input int A, B, C,
    input logic X, clk,
    output int S);

reg int precomputed;

always @ (posedge clk) begin
	precomputed <= B + C;
end

always @ (posedge clk) begin
    if (X==1) begin
        S <= A;
    end else begin
        S <= precomputed;
    end
end
endmodule
```

## What is the disadvantage of improving the design for max clock frequency?
* B and C need to be stable one clock cycle before X is set to anything other than 1.