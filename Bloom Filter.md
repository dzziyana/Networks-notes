> [!definition]
> - probabilistic data structure for set membership testing
> 	- useful for cache filtering (i.e. querying whether object is in cache with high probability)

# Use cases of Bloom Filter
* Bloom filters are used for pre-filtering. If there is a cache server, a bloom filter can be implemented on the NIC to filter out requests for entries that are certainly not in cache and thus, reduce latency and the overall load on the server’s CPU.
* Bloom filters are used in **network switches** to track specific information about network flows. Also, instead of deploying a filter on a NIC, the filter can be installed on a switch that connects multiple cache servers. Thus, the same effect can be achieved as in the previous example, just at the switch, which further improves the latency.

![[Pasted image 20250723171518.png]]

# Params
![[Pasted image 20250801094909.png]]