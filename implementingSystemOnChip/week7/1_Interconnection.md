# Block Interconnection
* The challenges with block interconnection can be a problem with:
	* Logical Interfacing: Regarding the standardization of interfaces.
	* Electrical Interfacing: Dealing with skew, round trip delays, drive capacity etc.

## Traditional Asynchronous Busses
![[Pasted image 20231228184419.png]]
* Is not directly connected to a clock.
* The operation is as such: 
	* The Chip Selection is asserted low.
	* A valid address is placed on the `address bus`. This is followed by the `read` signal going low.
	* The read signal remains low until read data's `data_in` is valid.
* This is used in ARM-FPGA interfaces and Framestore SRAM.
* Alternatively, a bidirectional bus can also be used which uses a Clock Enable signal and a direction signal.

## When to use Bidirectional vs Unidirectional
* Off chip interfaces use bidirectional due to pin restriction and wiring on the PCB.
* On chip busses use unidirectional to allow for many electrical buffers to be inserted along the wire to keep switching speeds reasonably rapid.