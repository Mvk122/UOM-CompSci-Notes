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
> Not part of the content:
* Delays can, however be created using shift registers to delay data by a certain number of clock cycles https://nandland.com/lesson-10-tutorial-shift-registers/

## Initialization
* When a state-holding element in switched on, it will settle into a stable binary state.
* It is not predictable what state this will be on an ASIC, so it is `unknown`.
* Hence initialisation is required in some cases i.e in ARM: 
	* R0-R14 start off as undefined.
	* R15 (PC) is initialized to 0.
* A rule of thumb is: 
	* Control registers should be initialized.
	* Data registers generally do not need to be initialized.

## Iffy Logic
* In digital simulation, an if statement can have 3 logic results instead of 2, `{0, 1, (x,z)` (unknown).
* `X`: Unknown or don't care.
* `Z`: High impedance, to indicate that a wire is not being driven by any component. This can be seen in busses where multiple components are connected to a wire but only one at a given time.
* To check for unknown, we can use different equality operators:
	* `== and !=` may return `{0, 1, x}`
	* `=== and !==` can only return `{0, 1}`