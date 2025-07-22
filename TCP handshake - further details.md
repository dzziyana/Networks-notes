# Reminder: 3-way handshake
> Client: SYN
> Server: SYN ACK
> Client: ACK
# The ISN
The sequence number in TCP is **not always set to 0** because of **practical and security reasons**:
### **1. Practical Issues:**
- TCP connections are identified using **IP addresses + port numbers**. However, port numbers **get reused** over time.
- If a new connection reuses the same **IP + port combination** as an old one, and sequence numbers were always 0, there is a risk that **old packets still in flight** (from the previous connection) could be mistakenly accepted in the new connection, leading to data corruption
### **2. Security Issues:**

- If TCP always started with **ISN = 0**, an **off-path attacker** (who cannot directly see the connection) could **guess sequence numbers** and inject malicious packets into the connection.
    
- By using a **predictable** sequence number, an attacker could **hijack the session** or **inject false data**.
    
### **Solution:**
- Instead of always using **0**, TCP sets the **Initial Sequence Number (ISN)** to a **randomized** value.
    
- The ISN is generated using a **pseudo-random number generator**, making it **unpredictable** and preventing attackers from easily forging TCP packets.
    
- During the **TCP handshake**, both sender and receiver **exchange ISNs** to synchronize communication properly.