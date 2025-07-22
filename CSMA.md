# ALOHA Protocol
> - works well at low load
> - inspired Ethernet
# Idea
Node just sends when it has traffic.
- If there was a collision (no ACK received) then wait a random time and resend
# CSMA (Carrier Sense Multiple Access)
- Improve Aloha by listening for activity before sending
	- Can do easily with wires, not wireless
*Still ***possible to listen and hear nothing*** when another node is sending because of delay*
## /CD (with collision detection)
- Can reduce the cost of collisions by detecting them and aborting (Jam) the rest of the frame time
	- Again, can be done with wires
	- used in [[Ethernet#Classical vs Modern Ethernet|classical Ethernet]]
### Complications
Want everyone who collides to know that it happened
- Time window in which a node may hear of a collision is 2D (2D = 2 $\times$ max. prop. delay = RTT) seconds
- Impose a minimum frame size that lasts for 2D seconds
	- So node can’t finish before collision
	- Ethernet minimum frame is 64 bytes
![[Pasted image 20250707113436.png]]

## CSMA "Persistance"
![[Pasted image 20250707113528.png]]
Problem is that multiple waiting nodes will queue up then collide
- More load, more of a problem
![[Pasted image 20250707113706.png]]

### Intuition for better solution
- If there are $N$ queued senders, we want each to send with probability $1/N$

### Binary Exponential Backoff 
Cleverly estimates the probability
- 1st collision, wait 0 or 1 frame times
- 2nd collision, wait from 0 to 3 times
- 3rd collision, wait from 0 to 7 times …

BEB doubles interval for each successive collision
- Quickly gets large enough to work
- Very efficient in practice
[[Ethernet]]
![[Pasted image 20250707115258.png]]