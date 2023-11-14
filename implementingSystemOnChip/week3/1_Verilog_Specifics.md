# Stylistic Pitfall 
```verilog
always @ (posedge clk)
	if (count < 9) count <= 1 + 1; else count <= 0;
```
* Due to the event driven architecture of verilog, non-blocking assignments occur after blocking assignments.
* Hence if the input, (count) is changed in a blocking assignment elsewhere in the code, that change will happen prior to this `if` statement even if it's condition is also `always @ (posedge clk)`.

# Delays
* Delays can be caused using `#value`.
* They cannot be synthesized and thus cannot be relied upon for functionality.
```verilog
#20 a = 11; // a is assigned to 11 after a delay of 20
wire #4 q; // There is a delay to any reassignment of q
assign q = a & b; // q cuanges 4 time steps after a or b changes
register <= #10 input_value; // There is a propogation delay when the input changes
```
* Delays can be used to:
	* model real components that have delays eg external memory reads.
	* Have cosmetic delays to make waveform traces more readable.
	* Sequence I/O in a test run.
* Delays cannot be accurately simulated in hardware due to manufacturing discrepancies.

## Initialisation
* When a state-holding element in switched on, it will settle into a stable binary state.
* It is not predictable what state this will be on an ASIC, so it is `unknown`.
* Hence initialisation is required in some cases i.e in ARM: 
	* R0-R14 start off as undefined.
	* R15 (PC) is initialized to 0.
* A rule of thumb is: 
	* Control registers should be initialized.
	* Data registers generally do not need to be initialized