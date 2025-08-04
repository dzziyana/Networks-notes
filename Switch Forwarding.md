Switch needs to find the right output port for the destination address in the Ethernet frame. How?
- Want to let hosts be moved around readily; don’t look at IP

# Backward learning
Switch forwards frames with a port/address table as follows:
1. To fill the table, it looks at the source address of input frames
2. To forward, it sends to the port, or else broadcasts to all ports

## ...with multiple switches
Just works with multiple switches and a mix of hubs _assuming no loops_, e.g., A sends to D then D sends to A
![[Pasted image 20250725120916.png]]

# Switch spanning tree
> How can we connect switches in any topology so they just work?
## The problem: forwarding loops
![[Pasted image 20250725121313.png]]
## Spanning tree solution
Switches collectively find a **spanning tree** for the topology
- A subset of links that is a tree (no loops) and reaches all switches
-  Switches forward as normal but only on spanning tree
-  Broadcasts will go up to the root of the tree and down all the branches
## Algorithm
Rules of the distributed game:
• All switches run the same algorithm
• They start with no information
• Operate in parallel and send messages
• Always search for the best solution

### Outline
1. Elect a root node of the tree (switch with the lowest address)
2. Grow tree as shortest distances from the root (using lowest address to break
distance ties)
3. Turn off ports for forwarding if they are not on the spanning tree
### Details
- Each switch initially believes it is the root of the tree
- Each switch sends periodic updates to neighbors with:
- Its address, address of the root, and distance (in hops) to root
- Switches favor ports with shorter distances to lowest root
- Uses lowest address as a tie for distances