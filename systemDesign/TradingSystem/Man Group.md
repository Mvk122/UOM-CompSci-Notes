* I've designed a cloud-native trading system with a focus on algorithmic trading that prioritises scalability and security in terms of:
	* Compute, through many horizontally scalable individual components.
	* People working on the system by abstraction of common trading functions like data cleaning, aggregation, signal generation and risk management, allowing for:
		* Faster development of trading strategies as quantitative developers will only need to focus on developing strategies.
		* A reduced risk of faults as people will only need to focus on their individual fields of expertise without having to consider the operations of the rest of the system.

* It all starts with the inputs to the system, market data, news or any other form of input coming as streams to our kafka producers.
* In Kafka, we can discard market data that is malformed from using UDP as opposed to TCP as well as filtering out any other invalid data.
* Furthermore, since all input data has to pass through kafka and given that we can easily scale kafka horizontally, it also makes sense compute aggregate data like the Relative Strength Index in the kafka layer to reduce latency.
* 