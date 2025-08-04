![[Pasted image 20250731162908.png]]
# Setting
Rule used at each node:
- Sends an incoming message on to all other neighbors
- Duplicate suppression
Inefficient because one node may ==receive== multiple copies of message
## Duplicate suppression
 Remember the message (using source and sequence number) so that it is only ==sent== once over each link 
## Stop-And-Wait
- Receiver acknowledges receipt, and sender resends if needed
