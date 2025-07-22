#AI-generated 
# Individual ACKs
- **Definition**: Each received packet is acknowledged **independently**, with its own ACK message.
- **Behavior**: For every packet with sequence number _N_, the receiver sends an ACK specifically for _N_.
## ✅ Pros:
- Simple to implement.
- Immediate feedback for each packet.
- Suitable for unreliable networks where loss detection must be fast.
## ❌ Cons:
- High overhead due to one ACK per packet.
- Inefficient for high-throughput networks.
## 📘 Example:
If packets with sequence numbers 1, 2, and 3 are received, the receiver sends:

```
ACK 1, ACK 2, ACK 3
```

---
# Cumulative ACKs
- **Definition**: Acknowledge **all packets up to and including** a certain sequence number.
    
- **Behavior**: An ACK for packet _N_ implies that all packets up to _N_ have been successfully received.
## ✅ Pros:
- Low overhead — fewer ACKs needed.
- Efficient in normal, in-order delivery scenarios.
## ❌ Cons:
- Does not inform sender about out-of-order or missing packets after _N_.
- Slower in detecting packet loss when packets arrive out of order.
#### 📘 Example:
If packets 1, 2, and 4 are received (packet 3 is missing), the receiver sends:

```
ACK 2
```

even though it already received 4 — because it’s still waiting for packet 3.

---
# Full Information ACKs (Selective ACKs / SACKs)
- **Definition**: ACKs carry **explicit information about all received packets**, including out-of-order ones.
    
- **Behavior**: The receiver informs the sender of **exact sequence numbers** of received packets, often via ranges.
#### ✅ Pros:
- Greatly improves performance in lossy or out-of-order networks.
- Helps sender retransmit only missing packets (no guessing).
#### ❌ Cons:
- More complex protocol logic.
- Slightly more overhead than cumulative ACKs due to added data fields.
#### 📘 Example:

If packets 1, 2, and 4 are received, the receiver might send:

```
ACK 2 (cumulative), SACK block: [4]
```

This tells the sender: “I’ve received up to 2 in order, and also packet 4, but 3 is missing.”

---
### Summary Table:

| Type            | ACKs Sent For     | Handles Out-of-Order? | Overhead | Efficiency |
| --------------- | ----------------- | --------------------- | -------- | ---------- |
| Individual ACKs | Each packet       | Yes                   | High     | Low        |
| Cumulative ACKs | Last in-order pkt | No                    | Low      | High       |
| Full Info ACKs  | Explicit packets  | Yes                   | Medium   | High       |
