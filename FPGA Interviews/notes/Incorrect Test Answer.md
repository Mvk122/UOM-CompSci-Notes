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