Distance vector routing uses a distributed version of Bellman-Ford algorithm and exhibits [[Slow convergence]]
# Setting
Each node computes its forwarding table in a distributed setting:
1. Nodes know only the cost to their neighbors; not the topology
2. Nodes communicate only with their neighbors using messages
3. All nodes run the same algorithm (distributed Bellman-Ford) concurrently
4. Nodes and links may fail, messages may be lost

# Algorithm
Each node maintains a **vector of distances** (the distance vector) to all destinations (also stores next hops for each destination)
1. Initialize vector with 0 (zero) cost to self, ∞ (infinity) to all other destinations
2. Periodically send vector to neighbors
3. Every round, after receiving vectors of all neighbors:
	- For each neighbor, ==add== cost of link to neighbor to the vector received from that neighbor
	- Set all vector entries _(except to self)_ to the minimum of all received values and set the corresponding neighbor as next hop

# Protocols looked at in the course:
[[RIP]]
