# Setting (same as [[Distance Vector Routing]])
1. Node knows only the cost to its neighbors; not the topology
2. Node can talk only to its neighbors using messages
3. Nodes run the same algorithm concurrently
4. Nodes/links may fail, messages may be lost

# Algorithm
### 1. Nodes [[Flooding|flood]] topology in the form of link state packets
	- Each node learns full topology
### 2. Each node computes its own forwarding table
	- By running Dijkstra (or equivalent)

![[Pasted image 20250731163810.png]]

# On change...
flood updated LSPs, and re-compute routes
# Complications
**Things that can go wrong:**
- Seq. number reaches max, or is corrupted
- Node crashes and loses seq. number
- Network partitions then heals
**Strategy:**
>==Include age== on LSPs and forget old information that is not refreshed!
# Protocols
[[OSPF]]
[[IS-IS]]
(They are also interior gateway protocols)
# Comparison to [[Distance Vector Routing]]
![[Pasted image 20250731164954.png]]