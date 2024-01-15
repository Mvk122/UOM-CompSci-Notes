# 1a
* Due to manufacturing discrepancies, it is impossible to make accurate delays.
* Delays should only be used in circuits to emulate delays from real components, simulate I/O or for aesthetic reasons.

# 1b
* When there is a variance in the clock signal's edges from their ideal position.
* The maximum allowable jitter is subtracted from the timing budget as jitter can cause a period to be too short, violating hold time constraints.

# 1c
* Test coverage in verification tries to ensure that every:
	* Branch
	* Line of code 
	* Path 
* Is executed to ensure that the device functions as the designer intended
* Verification checks for manufacturing defects and aims to test that every component is functional as well as ensuring that every component adheres to the requirements:
	* Timing 
	* Heat
	* Power 
	* Electrical 

# 1d
* The time after the clock that the data needs to be stable for the flip flop to read the value.

# 1e
* It is to tell the synthesizer that in the default case, we don't care what the output is. This prevents it from creating a latch.

# 1f
* The short circuit power dissipation wherein during switching, both pmos and nmos are conducting hence current goes from VDD to ground.
* Current required from resistance when switching. 
* The most important is the voltage which switching resistance is impacted by the square of. This is because it has the largest impact.

# 1g
* More manufacturing processes and expensive machinery are needed as chips have become smaller. 
* There is more variability in these smaller components. 
* It is hard to make optics for light to focus them more than they already are.

# 1h
* Tests to ensure that current features aren't broken/ removed while new changes to the code/design are being made.

# 1i 
* Synchronous
```verilog
module synchronous (
	input wire d,
	input wire clk,
	input wire read_enable,
	input wire reset,
	output reg q
);
	always @ (posedge clk) begin
	if (reset) q <= 0;
	else if (read_enable) q <= d;
	end

endmodule

module synchronous (
	input wire d,
	input wire clk,
	input wire read_enable,
	input wire reset,
	output reg q
);
	always @ (posedge clk, posedge reset) begin
	if (reset) q <= 0;
	else if (read_enable) q <= d;
	end

endmodule
```

# 1j
* It is sometimes better for components of a chip such as RAM to be implemented/ manufactured through a different process not using standard gates to be then copied and pasted as necessary as part of the design.

# 2a
TODO

# 2b
* The wider a transistor, the higher impedance and drive it has.

# 2c 
no idea 

# 2d
* The capacitance of the wire will be large hence the edges will be slower thus:
	* The device will operate slower as it takes longer for a 0 to settle to a 1.
	* Noise has a bigger impact.

# 2e
* Buffer insertion after the P&R stage.

# 2f
* If power efficiency is the goal, then more of the transistors should be high threshold as it reduces the power loss from short circuit.
* The design can be reviewed to see where changes can be made to use high T instead of low T.
	* Can be done by reducing the clock speed.


# 3a
