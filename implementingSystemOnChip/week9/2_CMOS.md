# CMOS Inverter
![[Pasted image 20240101210059.png]]
* By connecting `pMOS` and `nMOS` in parallel, we can create a `CMOS` inverter.
* We need to use both as `pMOS` is bad at transmitting 0 and `nMOS` is bad at transmitting 1 hence they complement each other.
* Though they are complementary enough with a `DC` signal, if the signal rapidly changed, the capacitive load on the output would slow down the output change.
	* Furthermore, the larger the load, the slower the output changes, hence if there is a large network fanout, larger transistors or transistors in parallel can be used to increase drive strength.
