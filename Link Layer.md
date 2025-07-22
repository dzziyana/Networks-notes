# Framing
...refers to the process of dividing the continuous stream of data from the network layer into manageable units called frames. These frames are used to encapsulate data with the necessary control information to ensure reliable communication. Framing is crucial for ***error detection, synchronisation, addressing, and flow control.*** 

We covered three different versions on how to address this problem:
1. Byte Count : Each frame has as length field.
2. Flags : Uses flag pattern ‘01111110‘ at beginning and end.
3. Stuffy Bits : Use escape pattern to escape flags appearing in the payload.

# Addressing
primarily achieved through the use of Media Access Control (MAC) addresses, which uniquely
identify each device on a local network. 
Protocols like [[ARP]] assist in mapping higher-layer addresses to MAC addresses

# Error Correction
- [[ARQ]]
## Hamming Codes
The idea is that we send ***check bits*** $R$, which are a function of the data bits D, i.e. $R= f(D)$.
In this context we define the 
### Hamming Distance, 
which is the minimum distance between any pair of strings. To determine the distance between two binary strings one can just count the digits where both differ.
![[Pasted image 20250722144741.png]]
### Error Detection : 
When all code-words of a mapping have the minimum hamming distance $d + 1$, we can detect up to $d$ errors.
### Error Correction : 
For a code of Hamming distance $2d + 1$, up to d errors can always be corrected by mapping to
the closest code-word
### Example
A possible mapping could be 0 → 000 and 1 → 111. Notice that all other binary strings of length 3 have no meaning in this mapping and thus one can conclude that they are corrupted if they occur. We can detect an error as long as the hamming distance is greater than the amount of errors occurred. Assume one wants to send a 0, which gets

![[Pasted image 20250722145244.png]]
Notice that we can detect up to 2 errors. Having 3 bit flips would not be recognized in this mapping.

[[Multiplexing]]
[[Multiple Access Protocols]]
[[CSMA]]

