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
* *