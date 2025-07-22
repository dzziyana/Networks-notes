The **congestion window (cwnd)** in TCP is a crucial part of **TCP congestion control**. It determines the 

==amount of data (in bytes) that a sender can transmit without receiving an acknowledgment (ACK) from the receiver.==

### **`cwnd` explained**

## **Flow Control vs. Congestion Control:**
- Flow Control: Managed by the ***receiver*** (via the receive window, `rwnd`) to prevent overwhelming it.
- Congestion Control: Managed by the ***sender*** (via `cwnd`) to prevent overloading the **network**.
## Adaptive Behavior:
- `cwnd` **dynamically** **adjusts** based on network conditions to optimize throughput while avoiding congestion.

## **Congestion Control Algorithms Affecting cwnd:**
    - **Slow Start:** `cwnd` starts small and exponentially increases.
    - **Congestion Avoidance:** `cwnd` increases linearly after a certain threshold (`ssthresh`).
    - **Fast Retransmit & Fast Recovery:** If packet loss occurs (detected via duplicate ACKs or timeouts), `cwnd` is reduced.
        
4. **Formula for Bandwidth Estimation:**
 $$   
\text{Throughput} \approx \frac{\text{cwnd}}{\text{RTT}}$$

    - Larger `cwnd` allows more in-flight packets, leading to better utilization of network capacity.

### **Practical Example:**

- A sender starts with `cwnd = 1 MSS` (Maximum Segment Size).
- For each ACK received, `cwnd` grows:
    
    - **Slow Start Phase:** `cwnd` doubles every RTT (`cwnd *= 2`).
        
    - **Congestion Avoidance Phase:** `cwnd` increases linearly (`cwnd += MSS` per RTT).
        
    - **Packet Loss:** `cwnd` is reduced (`cwnd /= 2` or `cwnd = 1 MSS` in severe cases).