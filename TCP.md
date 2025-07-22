# short info
uses [[ARQ#Selective repeat|Selective repeat]] and [[ACKing strategies#Cumulative ACKs|cumulative acks]]
# Header
![[Pasted image 20250325142235.png]]
## Header anatomy (closer look)
![[Pasted image 20250325173837.png]]
## Advertised Window
Advertised Window, $W$ = available space in **receiver buffer** 
Can send $W$ bytes beyond the next expected byte
**Limits number of bytes sender can have in flight**

- The receiver continuously updates and sends the available space in its buffer (i.e., the advertised window) to the sender using the TCP ==**window size field** in the TCP header.==
    
- **Sender Limitation**: The sender can only send as much unacknowledged data as the advertised window allows.
### Receiver buffer 
The receiver allocates a buffer to store incoming TCP data before the application processes it.

### Effects of $W$ on speed of data transfer 

$$
speed_{transfer} = min(W/RTT,B)
$$
### **Difference Between [[Congestion Window#**Flow Control vs. Congestion Control **|Receiver Window]] and Advertised Window in TCP**

| **Concept**    | **Receiver Window**                                                          | **Advertised Window**                                                                   |
| -------------- | ---------------------------------------------------------------------------- | --------------------------------------------------------------------------------------- |
| **Definition** | The actual available space in the receiver's buffer at any given moment.     | The value that the receiver communicates to the sender to control the data flow.        |
| **Visibility** | Internal to the receiver, not directly shared with the sender.               | Explicitly sent to the sender via the TCP header (Window Size field).                   |
| **Updates**    | Continuously changes as data is received and processed.                      | Periodically updated and sent in ACK packets to inform the sender.                      |
| **Function**   | Represents the real-time capacity to accept more data.                       | Acts as a flow control mechanism to prevent sender overflow.                            |
| **Example**    | If the receiver buffer has **50 KB free**, the receiver window is **50 KB**. | The receiver might advertise **50 KB**, or a slightly lower value, to ensure stability. |

### **Key Relationship:**

- The **advertised window** is the value of the **receiver window** that the receiver reports to the sender.
    
- In most cases, **advertised window ≤ receiver window** because the receiver may delay updating the sender to ensure smooth data flow.
    
- If the **advertised window reaches zero**, the sender stops sending data (TCP Zero Window condition) until it is updated.

## TCP Segment
![[Pasted image 20250325142511.png]]

### **ACK (Acknowledgment) in TCP: How It Works**

In **TCP (Transmission Control Protocol)**, **ACKs (Acknowledgments)** are used to confirm the successful receipt of data and ensure reliable communication between sender and receiver. The **ACK mechanism** helps prevent **data loss**, supports **flow control**, and manages **congestion control**.

---

### TCP Acknowledgment Mechanism - [[ACKing strategies#Cumulative ACKs|Cumulative ACKs]]

TCP uses **sequence numbers** and **ACK numbers** to track data segments.

- **Sequence Number (SEQ)**: Identifies the first byte in a segment
- **Acknowledgment Number (ACK)**: Indicates the next byte the receiver expects.

**Example**:  
If a sender transmits **1000 bytes** starting at **sequence number 1**, the receiver will send:
`ACK = 1001`

This means:  
_"I successfully received all bytes up to 1000, and I expect the next byte to be 1001."_

---

# TCP Handshake - [[TCP handshake - further details|3-Way Handshake]]**

ACK is used during the **TCP 3-way handshake** to establish a connection.

1. **Client → Server**: `SYN (SEQ/ISN_C = x)`
2. **Server → Client**: `SYN-ACK (SEQ/ISN_S = y, ACK = x+1)`
3. **Client → Server**: `ACK (SEQ = x+1, ACK = y+1)`
(SYN and ACK are both flags that can be set on TCP segments)

**This ensures both sides agree on starting sequence numbers.**

> The TCP handshakes usually only needs one RTT because data can already be sent "attached" to the first ACK (this is called *piggybacking*), else it needs 1.5 RTT


## Timeouts and Retransmissions
Retransmission of packet containing “next byte” when timer goes off. TCP uses [[Retransmission algorithms]]
TCP resets timer whenever new data is ACK-ed
# Further TCP topics
[[TCP - RTT estimation]]
[[TCP congestion control]]
[[TCP handshake - further details]]