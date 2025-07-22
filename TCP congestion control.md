The congestion control algorithm (CCA) employed by TCP is loss-based and thus cannot achieve the Kleinrock Optimum (Latency-based algorithm can) Furthermore, it also is inherently Round-Trip Time (RTT) unfair. This happens since transmissions with smaller RTTs increase the swnd faster. It is classified as an Additive-Increade-Multiplicative-Decrease (AIMD)
# Phases & Fast Recovery
TCP congestion control has **four main phases** to manage data flow and prevent network congestion:  

1. **Slow Start (SS)**
2. **Congestion Avoidance (CA)**
3. **Fast Retransmit (FR)**
4. **Fast Recovery (FRec)**  
---
### Initialising the algorithm
```
cwnd = 1, ssthresh = infinite
```
## Slow Start (SS) - Exponential Growth
```
if (cwnd < ssthresh ):
cwnd = cwnd + 1
```
### When?  
  - At the start of a connection **OR after a timeout.**
### How?
  - TCP begins with a small congestion window (**cwnd = 1 MSS**).  
  - **cwnd doubles** every **RTT** (exponential growth) until it reaches **ssthresh**. 
  >	The increase is exponential since the cwnd is incremented for every received ACK. Which means with a `swnd` of `x` we also (ideally) get `x` ACKs and thus increment `swnd` to `2x`

### Exit Condition
  - If **cwnd ≥ ssthresh**, switch to **Congestion Avoidance**.
  - If **packet loss occurs (timeout or triple duplicate ACKs)**, switch to **Fast Retransmit**.

---

## Congestion Avoidance (CA) - Linear Growth
```
else:
	cwnd = cwnd + 1/ cwnd
dup_ack = 0
```
### When? 
  - After Slow Start, when **cwnd ≥ ssthresh**.  
### How?
  - Instead of exponential growth, TCP increases **cwnd by 1 MSS per RTT** (linear).  
### Exit Condition
  - If packet loss is detected: 
    - **Triple duplicate ACKs → Fast Retransmit & Fast Recovery.**  
    - **Timeout → Slow Start.**

==Multiplicative Decrease== defines the rate for which we indirectly regulate `cwnd`. It uses ==timeouts== as an indicator for strong congestion. As a consequence it halves the `ssthresh`, which lowers the phase of exponentially-fast increase.
```
On Timeout:
	ssthresh = cwnd /2
	cwnd = 1
```
---
## Fast Retransmit (FR) - Quick Packet Recovery
### When?
  - If **triple duplicate ACKs** are received (indicating packet loss).  
### How?
  - Instead of waiting for a timeout, TCP **immediately retransmits** the lost packet.  
  - Then enters **Fast Recovery** to avoid returning to Slow Start.  
---

## Fast Recovery (FRec)
```
Duplicate ACKs received :
	dup_ack++;
	if (dup_ack >= 3):
		ssthresh = cwnd /2
		cwnd = ssthresh
```
### When?
  - Right after **Fast Retransmit**.  
### How?
  - Since triple duplicate ACKs indicate some packets are still getting through, TCP **assumes the network isn’t fully congested**.  
  - Instead of going back to **cwnd = 1 MSS**, TCP:  
    1. **Halves ssthresh** (ssthresh = cwnd / 2).  
    2. **Sets cwnd = ssthresh + 3 MSS** ==(since three duplicate ACKs suggest packets are flowing). ==
    3. **For each additional duplicate ACK, increases cwnd by 1 MSS**.  
    4. When a **new ACK arrives (not a duplicate), TCP exits Fast Recovery** and enters **Congestion Avoidance**.  

### Exit Condition
  - When the sender receives a **new ACK** (not a duplicate).  
  - Then TCP resumes **Congestion Avoidance**.
## Visualization
![[Pasted image 20250709181609.png]]
### **Summary of TCP Phases**
| **Phase**                     | **Growth Pattern**                                     | **Entry Condition**                  | **Exit Condition**                                |
| ----------------------------- | ------------------------------------------------------ | ------------------------------------ | ------------------------------------------------- |
| **Slow Start** (SS)           | **Exponential (cwnd × 2 per RTT)**                     | Start of connection OR after timeout | **ssthresh reached** → CA OR **packet loss** → FR |
| **Congestion Avoidance** (CA) | **Linear (cwnd + 1 MSS per RTT)**                      | cwnd ≥ ssthresh                      | **Packet loss** → FR (dup ACKs) OR SS (timeout)   |
| **Fast Retransmit** (FR)      | **Immediate retransmission**                           | 3 duplicate ACKs received            | Enters Fast Recovery                              |
| **Fast Recovery** (FRec)      | **cwnd = ssthresh + 3 MSS, grows with duplicate ACKs** | After Fast Retransmit                | New ACK received → CA                             |

---

### **Algorithms**

1. **Tahoe**
    - Uses **Slow Start, Congestion Avoidance, and Fast Retransmit**.
    - On loss, reduces congestion window (cwnd) to **1** and restarts **Slow Start**.
        
2. **Reno**
    - Improves Tahoe by adding **Fast Recovery**, reducing **cwnd by half** instead of resetting to 1.
    - More efficient in high-bandwidth scenarios.
        
3. **New Reno**
    - Enhances Reno by **better handling multiple packet losses** in a window.
    - Avoids reducing cwnd multiple times for different lost packets.
        
4. **Vegas**
    - Proactively detects congestion before packet loss.
    - Uses **round-trip time (RTT) variations** to adjust the sending rate.
    - More stable but underutilizes bandwidth in some cases.
        

---

### **4. Modern Congestion Control Algorithms**

- **Cubic TCP:** Used in Linux, increases cwnd aggressively when large, but conservatively when small.
    
- **BBR (Bottleneck Bandwidth & RTT):** Measures available bandwidth instead of relying on loss-based control.
    
- **QUIC Congestion Control:** Used in HTTP/3; improves upon TCP’s limitations