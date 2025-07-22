...builds up on [[UDP]]: the actual QUIC header and data is stored in the UDP data segment. This makes a UDP package indistinguishable from an QUIC Package at first glance. 
# 0 RTT handshake
The client sends a Client Hello packet to the server. This packet includes the initial data and requests a connection to the server. If supported and allowed by the server, the client can send encrypted data (early data) along with the Client Hello. This allows the client to start sending application data immediately without waiting for the handshake to complete.
# Advantages over TCP
- ==Faster connection== establishment : QUIC has an 1-RTT Handshake and 0-RTT for all subsequent connections
-  ==Better privacy== and mobility : CIDS are independant of the IP address, which allows better mobility and security, as the address can be hidden. For that UDP sockets are used.
- ==Prevents [[Sliding window paradigm#Head of line blocking|head of line blocking]]== by introducing *logically independent streams*
# Multiple independent streams
#TODO

### **Has QUIC Replaced the Conventional Stack?**
🔹 Not completely, but it's replacing TCP+TLS+HTTP/2 for many applications
🔹 QUIC integrates **transport (TCP-like) and security (TLS) into one protocol**  
🔹 HTTP/3 **requires QUIC**, so any website using HTTP/3 is using QUIC instead of TCP

#### What QUIC replaces
- **TCP** (QUIC runs over UDP, implementing its own congestion control)
- **TLS 1.3** (QUIC encrypts all transport headers and payloads)
- **HTTP/2** (QUIC is the foundation of HTTP/3)
#### What QUIC does not replace (yet)
- **TCP for non-HTTP traffic** (e.g., SSH, FTP, SMTP still use TCP)
- **Lower-level transport protocols** (e.g., QUIC runs over UDP, it doesn’t replace IP)
- **TCP in legacy systems** (many networks still rely on TCP-based protocols)

#AI-generated 
### **Why QUIC is Better Than TCP+TLS**

🚀 **Faster Connection Setup**
- **1 RTT instead of 3** (TCP + TLS handshake takes more time)
- **Zero RTT resumption** (resuming a previous connection needs no round trips)

🔥 **Solves Head-of-Line Blocking**
- In TCP, if one packet is lost, everything **stalls**.
- In QUIC, streams are independent → one lost packet **doesn’t block others**.
    
🔐 **Better Security (Always Encrypted)**
- QUIC **encrypts** even transport-layer headers, making traffic analysis harder.
- Unlike TCP+TLS, where some metadata is visible, QUIC makes **everything private**.
    
📡 **Better for Mobile & High-Latency Networks**
- TCP connections **break when switching networks** (e.g., Wi-Fi → 4G).
- QUIC has **Connection IDs**, so switching networks doesn’t disrupt connections.