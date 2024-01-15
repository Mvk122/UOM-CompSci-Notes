# 1a
* Simultaneous instruction multiple data, where one operation is done on multiple data at once.
* It is used in GPUs to process many pixels with the same operation at once.

## 1b
1. bbb becomes input_2
2. ccc becomes aaa's orignal value
3. aaa becomes input_1
4. ddd becomes input_2

## 1c
* Power gating is when a pMOS (or less commonly nMOS) transistor is used to send power to a component only when it is needed, reducing overall power consumption.=
* When the microcontroller needs to be used, there will be latency starting it up as needed.

## 1d
* 200Mbytes per second.

# 1e
* It means don't care, so the synthesizer can optimise the logic further.
* It means unknown value, suggesting an error condition.

# 1f
* Greater drive strength through higher transconductance.
* Better to carry high voltages

# 1g
* Buffer insertion, which is used to speed up transitions when there is a high conductance from long wires, it is used to speed up edges, making the device faster and reduce the impact of noise.

# 1h
* Verification is used to check that the design works as the designer intended, testing is used to check that the manufactured product is not defective in its outputs.
* When testing, it tries to have as much coverage of the logical units as possible to ensure all the manufactured units work.

# 1i
* The voltage at which pMOS or nMOS starts conducting.
* The voltage at which a digital signal is considered a 1 or a 0.

# 1j
* There are no control signals for burst sizes etc.
* It is useful for slow, less complicated peripheral devices.

# 2a
* Leads to a simplification in the design process as we can assume that latches/ registers set in the current clock cycle are set at the next clock cycle. 
* Allows for FSMs where a snapshot of the current state and inputs can be used to derive the next state.
* Timing is quantized

## 2b 
* The timing difference between the arrival of a clock signal at different parts of the circuit.

# 2c
* All stages of the pipeline take up the same amount of time.

# 2d 
* A process known as time stealing can be used wherein: 
	* The clock speed is sped up to its required amount.
	* The additional time can be `stolen` from its neighbour that reads from the register by adding a delay to the output register of the memory macrocell. 
	* Since the neighbour uses less time than the faster clock period, there is no timing violation in the circuit.

# 2e
* First design advantages:
	* Synchronous design that is easier to reason about as it only has 1 clock.\
	* Since the register is only enabled w
* First design disadvantages: 
	* More wiring is needed
* Second design advantages:
	* Fewer wiring is needed
	* Uses less power as the clock signal does not need to be distributed to the register.
* Second design disadvantages:
	* Uses multiple clocks and is hard to reason about especially when creating the timing constraint. 
* I would use the first design as:
	* FPGA's already implement the enable register in hardware, making it faster and more power efficient. 
	* The design is easier to reason about. 

# 2f
* Easier to divide down than multiply up and the clock frequency can be divided by 2 with each ripple counter.

# 3a
