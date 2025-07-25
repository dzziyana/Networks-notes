# Framing
...refers to the process of dividing the continuous stream of data from the network layer into manageable units called frames. These frames are used to encapsulate data with the necessary control information to ensure reliable communication. Framing is crucial for ***error detection, synchronisation, addressing, and flow control.*** 

We covered three different versions on how to address this problem:
## 1. Byte Count :
Each frame has as length field.
## 2. Flags : 
Uses flag pattern ‘01111110‘ at beginning and end.
## 3. Bit stuffing / Stuffy Bits :
Use escape pattern to escape flags appearing in the payload.

# Addressing
primarily achieved through the use of Media Access Control (MAC) addresses, which uniquely
identify each device on a local network. 
Protocols like [[ARP]] assist in mapping higher-layer addresses to MAC addresses

# Error Correction
- [[ARQ]]
- [[Hamming Codes]]

# Avoiding concurrency
[[Multiplexing]]
[[Multiple Access Protocols]]
[[CSMA]]
