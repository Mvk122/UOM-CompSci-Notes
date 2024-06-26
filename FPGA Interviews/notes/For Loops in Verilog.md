* For loops in verilog are executed at synthesis time wherein they are unrolled and synthesised into hardware that operates in parallel.
* Due to the for loop synthesising into hardware, they can only be of a fixed length.
* For loops in verilog can have `break` statements, which instructs it to accept the prior iterations as precedent.
```verilog
module onehot_to_binary (
	input clock,
	input logic [31:0] input_data,
	input logic reset,
	output logic [4:0] output_data
);

always @(posedge clock) begin
	if (reset == 1) begin
		output_data <= 0;
	end else begin

	for (int i = 0; i < 32; i++) begin
		if (input_data[i] == 1) begin
		output_data <= i;
		break
		end
	end
endmodule
```