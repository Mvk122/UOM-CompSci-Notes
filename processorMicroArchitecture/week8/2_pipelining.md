# Pipelining

* Pipelining can be used to `partition` a system by introducing parallelism to increase the `throughput` of a design.
* This comes at the cost of higher latency as latches are added: 
    * Creating a longer path
    * There is a requirement of them to slow the flow down to make each stage take the time of the slowest logic block to ensure the stages are synchronized.