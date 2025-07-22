Automatic Repeat reQuest is the general concept of providing reliability by using re-transmissions. A packet is re-sent when the timer runs out for the corresponding acknowledgment (ACK) packet. 
- Depending on the context we have to use [[ACKing strategies|different Acks]]. 

It provides the reliability in the transport layer and is used in the [[Sliding window paradigm]] as well as in TCP, QUIC. *(UDP does not use ARQ)*

# Variants
## Stop-and-Wait Protocol
In this version, the sender transmits a single packet and waits for an acknowledgment (ACK) before sending the next packet.
If an ACK is not received within a certain timeout period, the packet is retransmitted. 
## Go-Back-N
Here, the sender can send multiple packets within a window size (N) without waiting for an ACK for each one. However, if a packet is lost or an error is detected, *all subsequent packets are retransmitted. **Thus, this version relies on cumulative ACKs.***
## Selective repeat
The sender also sends multiple packets within a window size. Unlike Go-Back-N, only the specific lost or erroneous packets are retransmitted based on individual ACKs and timers, making it more eﬀicient. This version normally uses only individual ACKs.
